def calcular_horas_trabalhadas(hora_entrada, hora_intervalo_inicio, hora_intervalo_fim, hora_saida):

  def validar_formato_hora(hora):
    try:
      horas, minutos = map(int, hora.split(':'))
      if 0 <= horas <= 23 and 0 <= minutos <= 59:
        return True
      else:
        return False
    except ValueError:
      return False

  if not validar_formato_hora(hora_entrada) or not validar_formato_hora(hora_intervalo_inicio) or \
     not validar_formato_hora(hora_intervalo_fim) or not validar_formato_hora(hora_saida):
    raise ValueError("Formato de hora inválido. Use HH:mm")

  def converter_para_minutos(hora):
    horas, minutos = map(int, hora.split(':'))
    return horas * 60 + minutos

  entrada_minutos = converter_para_minutos(hora_entrada)
  intervalo_inicio_minutos = converter_para_minutos(hora_intervalo_inicio)
  intervalo_fim_minutos = converter_para_minutos(hora_intervalo_fim)
  saida_minutos = converter_para_minutos(hora_saida)

  minutos_trabalhados_sem_intervalo = saida_minutos - entrada_minutos
  minutos_intervalo = intervalo_fim_minutos - intervalo_inicio_minutos

  minutos_trabalhados = minutos_trabalhados_sem_intervalo - minutos_intervalo

  horas_trabalhadas = minutos_trabalhados // 60
  minutos_trabalhados %= 60

  return "{:02d}:{:02d}".format(horas_trabalhadas, minutos_trabalhados)

# Testes Unitários
def test_calcular_horas_trabalhadas():
  assert calcular_horas_trabalhadas("08:00", "12:00", "13:00", "17:00") == "08:00"
  assert calcular_horas_trabalhadas("10:30", "14:00", "14:30", "18:00") == "07:00"
  assert calcular_horas_trabalhadas("09:00", "12:30", "13:30", "17:30") == "07:30"

  try:
    calcular_horas_trabalhadas("08", "12:00", "13:00", "17:00")
  except ValueError as e:
    assert str(e) == "Formato de hora inválido. Use HH:mm"

  try:
    calcular_horas_trabalhadas("08:00", "12", "13:00", "17:00")
  except ValueError as e:
    assert str(e) == "Formato de hora inválido. Use HH:mm"

  try:
    calcular_horas_trabalhadas("08:00", "12:00", "13", "17:00")
  except ValueError as e:
    assert str(e) == "Formato de hora inválido. Use HH:mm"

  try:
    calcular_horas_trabalhadas("08:00", "12:00", "13:00", "17")
  except ValueError as e:
    assert str(e) == "Formato de hora inválido. Use HH:mm"


if __name__ == "__main__":
  test_calcular_horas_trabalhadas()

  hora_entrada = input("Digite a hora de entrada (HH:mm): ")
  hora_intervalo_inicio = input("Digite a hora de início do intervalo (HH:mm): ")
  hora_intervalo_fim = input("Digite a hora de fim do intervalo (HH:mm): ")
  hora_saida = input("Digite a hora de saída (HH:mm): ")

  try:
    horas_trabalhadas = calcular_horas_trabalhadas(hora_entrada, hora_intervalo_inicio, hora_intervalo_fim, hora_saida)
    print("Horas trabalhadas:", horas_trabalhadas)
  except ValueError as e:
    print("Erro:", e)
