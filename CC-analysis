import re

def extrair_informacoes(arquivo_entrada, encoding='utf-8'):
    padrao = re.compile(r'C\.C: (\d+) // VAL: (\d+) // C\. SEG: (\d+)')
    informacoes = set()  # Usando um conjunto para evitar repetições

    try:
        with open(arquivo_entrada, 'r', encoding=encoding) as arquivo:
            for linha in arquivo:
                correspondencia = padrao.search(linha)
                if correspondencia:
                    cc, val, c_seg = correspondencia.groups()
                    informacoes.add(f'C.C: {cc} // VAL: {val} // C. SEG: {c_seg}')
    except FileNotFoundError:
        print(f"O arquivo {arquivo_entrada} não foi encontrado.")
    except UnicodeDecodeError:
        print(f"Erro de decodificação: não foi possível decodificar o arquivo {arquivo_entrada} usando a codificação {encoding}.")

    return informacoes

def salvar_em_txt(informacoes, nome_txt='resultado.txt'):
    with open(nome_txt, 'w', encoding='utf-8') as arquivo_txt:
        for info in informacoes:
            arquivo_txt.write(info + '\n')

if __name__ == "__main__":
    arquivo_entrada = "arquivo_entrada.txt"
    informacoes = extrair_informacoes(arquivo_entrada)
    salvar_em_txt(informacoes, "arquivo_saida.txt")
