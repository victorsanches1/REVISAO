# REVISAO
pedidos = [
{'cliente':'Ana',
'itens':[{'prato':'Lasanha','preco':30},
{'prato':'suco de laranja','preco':10}]},

{'cliente':'Robespierre',
'itens':[{'prato':'Pizza','preco':50},
{'prato':'suco de laranja','preco':8},
{'prato':'Sobremesa','preco':20}]},
   
    {'cliente':'Rousseau',
'itens':[{'prato':'Pizza','preco':50},
{'prato':'suco de laranja','preco':10}]}]


def calcular_gasto_cliente(lista_pedidos, nome_cliente):
    total_cliente=0
    for pedido in lista_pedidos:
        if pedido['cliente'] == nome_cliente:
            for item in pedido['itens']:
                total_cliente += item['preco']
    return total_cliente

def prato_mais_vendido(lista_pedidos):
    pratos = {}
    for pedido in lista_pedidos:
        for item in pedido['itens']:
            prato = item['prato']
            if prato in pratos:
                pratos[prato] += 1
            else:
                pratos[prato]=1
    prato_campeao = max(pratos, key = pratos.get)
    return prato_campeao

def maisGastaram(lista_pedidos):
    gastoTotal= {}
    
    for pedido in lista_pedidos:
        cliente = pedido['cliente']
        total_do_pedido = sum([item['preco'] for item in pedido['itens']])
        gastoTotal[cliente]= total_do_pedido

    ranking_completo = sorted(gastoTotal.items(), key=lambda item: item[1], reverse=True)
    top_3 = ranking_completo[:3]
    
    return top_3

print(maisGastaram(pedidos))



# 2 

atletas = [ { 'nome':'Lucas','idade':20,
'modalidades':['Natação','Corrida'],
'treinos':{'Natação':12,'Corrida':8}},

{'nome': 'Mariana','idade':25,
'modalidades':['Musculação','Yoga','Pilates'],
'treinos':{'Natação':15,'Yoga':10,'Pilates':5}},

{'nome':'João',
'idade':22,
'modalidades':['Corrida','Ciclismo'],
'treinos':{'Corrida':20,'Ciclismo':18}}]


def mediaIdade(atletas):
    esporte = input('Insira o esporte para ver a media de idade dele:')
    idades = []
    for atleta in atletas:
         if esporte in atleta['modalidades']:
            idades.append(atleta['idade'])
    else:
        print('atleta nao encontrado!')
    
    if len(idades)> 0:
     media = sum(idades)/len(idades)
    return media
    

def esporte_mais_treinado(atletas):
   esportista = input('Escolha o atleta para ver qual esporte ele mais treinou:')
   for atleta in atletas:
      if esportista == atleta['nome']:
         maisTreinado = max(atleta['treinos'], key = atleta['treinos'].get  )
   return maisTreinado

def mais_de_2(atletas):
   mais2 = []
   for atleta in atletas:
      if len(atleta['modalidades']) > 2:
         mais2.append(atleta['nome'])
   return mais2

media = (mediaIdade(atletas))
print(f'A media de idades neste esporte é:{media}')
esporte_mais =(esporte_mais_treinado(atletas))
print(f'O esporte mais treinado pelo atleta selecionado é:{esporte_mais}')
mais_de2 = mais_de_2(atletas)
print(f'Lista de atletas que praticam mais de 2 esportes:{mais_de2}')


# 3 
musicas = [
{'titulo':'Back in Black',
'artista':'AC/DC',
'downloads':6800,
'avaliacoes':[5,4,5,5,4,5]},

{'titulo':'Stairway to Heaven',
'artista':'Led Zeppelin',
'downloads':8900,
'avaliacoes':[5,5,4,5,5,5]},

{'titulo':'Enter Sandman',
'artista':'Metallica',
'downloads':8100,
'avaliacoes':[5,5,5,4,4,5]}]

def mediaAvaliacao(musicas):
    medias = {}
    for musica in musicas:
        music = musica['titulo']
        ava = musica['avaliacoes']
        media = sum(ava)/len(ava)
        medias[music] = media
    return medias

def maior_downloads(musicas):
    downloads = {}
    for musica in musicas:
        artista = musica['artista']
        downloadsMusica = musica['downloads']
        if artista in downloads:
            downloads[artista] += downloadsMusica
        else:
            downloads[artista] = downloadsMusica
        

    maior = max(downloads.items(), key = lambda download: download[1])
    return maior

def ranking_avaliacoes(musicas):
    medias = {}
    for musica in musicas:
        music = musica['titulo']
        ava = musica['avaliacoes']
        media = sum(ava)/len(ava)
        medias[music] = media
    ranking = sorted(medias.items(), key = lambda media:media[1], reverse=True)
    return ranking
        

medias=(mediaAvaliacao(musicas))
print(f'As medias das avaliações de cada musica foram:{medias}')
maiorTotal = (maior_downloads(musicas))
print(f'O maior numero de downloads foi{maiorTotal}')
rank = (ranking_avaliacoes(musicas))
print(f'Segue em ordem o rank dos mais bem avaliados: {rank}')


# 4

filmes = [
{'titulo':'Inception',
'diretor':'Cristopher Nolan',
'bilheteria':830,
'avaliacoes':[9,10,8,9,10]},

{'titulo':'Avengers: Endgame',
'diretor':'Anthony Russo',
'bilheteria':2797,
'avaliacoes':[9,9,10,10,9]},

{'titulo':'The Dark Knight',
'diretor':'Cristopher Nolan',
'bilheteria':1005,
'avaliacoes':[10,10,9,10,10]},

{'titulo':'Jurassic Park',
'diretor':'Steven Spielberg',
'bilheteria':1029,
'avaliacoes':[8,9,9,8,9]}]

def top_bilheteria(filmes):
    filme_bilheteria = {}
    for filme in filmes:
        nome = filme['titulo']
        filme_bilheteria[nome]= filme['bilheteria']
    rank = sorted(filme_bilheteria.items(), key= lambda filme: filme[1], reverse = True)
    rank_3 = rank[:3]
    return rank_3

def top_avaliacao(filmes):
    filmes_media = {}
    for filme in filmes:
        nome = filme['titulo']
        avaliacao= filme['avaliacoes']
        media = sum(avaliacao)/len(avaliacao)
        filmes_media[nome]= media
    ranking = sorted(filmes_media.items(), key= lambda filme: filme[1], reverse = True)
    rank_3 = ranking[:3]
    return rank_3

def bilheteria_por_diretor(filmes):
    diretor_totalDaBilheteria = {}
    for filme in filmes:
        diretor = filme['diretor']
        bilheteria = filme['bilheteria']
        if diretor in diretor_totalDaBilheteria:
            diretor_totalDaBilheteria[diretor] += bilheteria
        else:
            diretor_totalDaBilheteria[diretor] = bilheteria
    return diretor_totalDaBilheteria

def campeao(filmes):
    filme_campeao = max(filmes, key=lambda filme: filme['bilheteria'] * (sum(filme['avaliacoes']) / len(filme['avaliacoes'])))
    return filme_campeao

rankdabilheteria = (top_bilheteria(filmes))
print(f'O rank dos 3 filmes com maior bilheteria esta em ordem decrescente a seguir:{rankdabilheteria}')
rank_avaliacao = (top_avaliacao(filmes))
print(f'O rank dos 3 mais bem avaliados esta em ordem decrescente a seguir:{rank_avaliacao}')
bilheteria = bilheteria_por_diretor(filmes)
print(f'Total de bilheteria por diretor:{bilheteria}')
print(campeao(filmes))
