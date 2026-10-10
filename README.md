# Idioma do Tempo (Chronolíngua)

Bem-vindo à documentação oficial do **Idioma do Tempo**, um sistema de cifra e escrita conceitual baseado na passagem das horas em relógios analógicos e na antiguidade dos algarismos romanos. 

Este sistema foi desenvolvido como uma linguagem críptica e de enigma para mensagens ocultas.

---

## ⚙️ Como Funciona a Cifra

O idioma traduz letras do alfabeto latino padrão ($A$ a $Z$) combinando duas coordenadas mecânicas:
1. **O Bloco (Numeral Romano):** Indica o terço do alfabeto em que a letra se encontra.
2. **A Posição (Hora do Relógio):** Indica a posição exata da letra dentro daquele bloco, indo da 1ª hora (I) até a 12ª hora (XII).

### Tabela de Mapeamento

| Relógio (Hora) | Bloco I (I) <br> *Letras A – L* | Bloco II (II) <br> *Letras M – X* | Bloco III (III) <br> *Letras Y – Z* |
| :---: | :---: | :---: | :---: |
| **I** | **A** | **M** | **Y** |
| **II** | **B** | **N** | **Z** |
| **III** | **C** | **O** | — |
| **IV** | **D** | **P** | — |
| **V** | **E** | **Q** | — |
| **VI** | **F** | **R** | — |
| **VII** | **G** | **S** | — |
| **VIII** | **H** | **T** | — |
| **IX** | **I** | **U** | — |
| **X** | **J** | **V** | — |
| **XI** | **K** | **W** | — |
| **XII** | **L** | **X** | — |

---

## 📝 Exemplo Prático

Para decodificar ou codificar uma palavra, basta separar cada letra pelas coordenadas `Bloco:Hora`.

Exemplo com a palavra **TEMPO**:
* **T** $\rightarrow$ Bloco II, Hora VIII $\rightarrow$ `II:VIII`
* **E** $\rightarrow$ Bloco I, Hora V $\rightarrow$ `I:V`
* **M** $\rightarrow$ Bloco II, Hora I $\rightarrow$ `II:I`
* **P** $\rightarrow$ Bloco II, Hora IV $\rightarrow$ `II:IV`
* **O** $\rightarrow$ Bloco II, Hora III $\rightarrow$ `II:III`

Resultado criptografado:
`II:VIII . I:V . II:I . II:IV . II:III`

---

## 🛠️ Script de Tradução (Python)

Se você quiser automatizar a tradução ou criar um decodificador próprio, utilize o script abaixo em Python:

```python
def traduzir_para_tempo(texto):
    texto = texto.upper().replace(" ", "")
    resultado = []
    
    for letra in texto:
        codigo_ascii = ord(letra)
        if 65 <= codigo_ascii <= 90: # A-Z
            posicao = codigo_ascii - 65
            if posicao < 12:
                bloco, hora = "I", posicao + 1
            elif posicao < 24:
                bloco, hora = "II", (posicao - 12) + 1
            else:
                bloco, hora = "III", (posicao - 24) + 1
            resultado.append(f"{bloco}:{hora}")
            
    return " . ".join(resultado)

# Exemplo:
print(traduzir_para_tempo("tempo"))
# Saída: II:VIII . I:V . II:I . II:IV . II:III
```

---
*Criado para fins de enigmas, ARGs e explorações narrativas.*
