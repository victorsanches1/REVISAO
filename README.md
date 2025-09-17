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
          
