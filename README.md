import requests

def converter_moeda(valor, moeda_origem, moeda_destino):
    # API pública para taxas de câmbio (pode requerer chave dependendo da versão)
    url = f"https://exchangerate-api.com{moeda_origem.upper()}"
    
    try:
        resposta = requests.get(url)
        dados = resposta.json()
        
        if moeda_destino.upper() not in dados['rates']:
            print(f"Moeda de destino '{moeda_destino}' não encontrada.")
            return None

        taxa = dados['rates'][moeda_destino.upper()]
        valor_convertido = valor * taxa
        return valor_convertido

    except Exception as e:
        print(f"Erro ao conectar com a API: {e}")
        return None

# Exemplo de Uso
valor_brl = 100
moeda_de = 'BRL'
moeda_para = 'USD'

resultado = converter_moeda(valor_brl, moeda_de, moeda_para)

if resultado:
    print(f"{valor_brl} {moeda_de} equivale a {resultado:.2f} {moeda_para}")
