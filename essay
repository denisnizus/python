import nltk
from nltk.tokenize import sent_tokenize, word_tokenize
from nltk.corpus import wordnet
from nltk.stem import WordNetLemmatizer

def evaluate_essay(essay):
    # Tokenização do texto em sentenças e palavras
    sentences = sent_tokenize(essay)
    words = word_tokenize(essay)
    
    # Cálculo da média do tamanho das sentenças
    sentence_lengths = [len(word_tokenize(sentence)) for sentence in sentences]
    avg_sentence_length = sum(sentence_lengths) / len(sentence_lengths)
    
    # Verificação do uso adequado de palavras-chave
    keywords = ['introdução', 'desenvolvimento', 'conclusão']
    keyword_count = sum([essay.lower().count(keyword) for keyword in keywords])
    
    # Verificação do uso de sinônimos
    lemmatizer = WordNetLemmatizer()
    lemmatized_words = [lemmatizer.lemmatize(word.lower()) for word in words]
    synonyms = set(wordnet.synsets(word))
    synonym_count = sum([len(set(wordnet.synsets(word))) > 0 for word in lemmatized_words])
    
    # Cálculo da nota final com base nos critérios
    length_score = min(avg_sentence_length / 20, 1)  # Normaliza a média do tamanho das sentenças em relação a 20
    keyword_score = min(keyword_count / 3, 1)  # Normaliza a contagem de palavras-chave em relação a 3
    synonym_score = min(synonym_count / len(lemmatized_words), 1)  # Normaliza a contagem de sinônimos em relação ao número total de palavras
    
    final_score = (length_score + keyword_score + synonym_score) / 3 * 10
    
    return final_score

# Exemplo de uso
essay = """
A educação é um tema de grande importância para o desenvolvimento de uma sociedade. 
Uma boa educação permite que os indivíduos adquiram conhecimentos e habilidades que são essenciais para seu crescimento pessoal e profissional. 
Além disso, a educação desempenha um papel fundamental na promoção da igualdade de oportunidades e no combate à exclusão social.
Neste texto, discutiremos a importância da educação, analisando seus benefícios e desafios.
"""

score = evaluate_essay(essay)
print("Nota do texto dissertativo:", score)
