---
title: 'Instrukcje: dostosowywanie wiązania udostępnionego przez system'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: cee570bdc9d7bf6debfc4ec226e91f3fd79a01dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095155"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Instrukcje: dostosowywanie wiązania udostępnionego przez system
Windows Communication Foundation (WCF) obejmuje kilka powiązania dostarczane przez system, które pozwalają na konfigurowanie niektórych właściwości podstawowych elementów powiązania, ale nie wszystkie właściwości. W tym temacie pokazano, jak ustawić właściwości na elementy powiązania do tworzenia niestandardowego powiązania.  
  
 Aby uzyskać więcej informacji na temat bezpośrednio utworzyć i skonfigurować elementy powiązania bez korzystania z powiązań dostarczanych przez system, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia i rozszerzanie powiązań niestandardowych, zobacz [rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 W programie WCF składają się wszystkie powiązania z *elementów wiązania*. Każdy element powiązania jest pochodną <xref:System.ServiceModel.Channels.BindingElement> klasy. Powiązania dostarczane przez system, takie jak <xref:System.ServiceModel.BasicHttpBinding> utworzyć i skonfigurować własne elementy powiązania. W tym temacie pokazano, jak uzyskać dostęp i zmiana właściwości tych elementów powiązania, które nie są bezpośrednio widoczne w powiązaniu; w szczególności <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Poszczególne elementy znajdują się w kolekcji, reprezentowane przez <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i zostaną dodane w następującej kolejności: Przepływ transakcji, niezawodnej sesji, zabezpieczeń, złożonego dupleks, jednokierunkowe zabezpieczeń Stream, kodowanie komunikatu i transportu. Należy zauważyć, że nie wszystkie elementy na liście są wymagane w każde powiązanie. Elementy powiązań zdefiniowanych przez użytkownika może również zostać wyświetlony w tej kolekcji element powiązania i musi znajdować się w tej samej kolejności, jak opisano wcześniej. Na przykład transportu zdefiniowanych przez użytkownika musi być ostatnim elementem w kolekcji elementów powiązania.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Klasa zawiera trzy elementy powiązania:  
  
1.  Opcjonalne zabezpieczeń powiązania elementu, albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> klasa używana do za pomocą transportu HTTP (zabezpieczeniami na poziomie wiadomości) lub <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> klasy, która jest używana, gdy warstwa transportu zapewnia zabezpieczeń, w tym przypadku transportu HTTPS jest używany.  
  
2.  Kodera komunikatów wymaganego elementu, powiązania albo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> lub <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Wymagane transportu elementu, powiązania albo <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, lub <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 W tym przykładzie firma Microsoft Utwórz wystąpienie obiektu powiązania, generowanie *niestandardowego powiązania* z niego, sprawdź elementy niestandardowego powiązania, a gdy okaże się element powiązania protokołu HTTP, firma Microsoft jego `KeepAliveEnabled` właściwość `false`. `KeepAliveEnabled` Właściwość nie jest uwidaczniana bezpośrednio na `BasicHttpBinding`, dzięki czemu możemy utworzyć niestandardowego powiązania, przejdź do elementu powiązania i ustawić tę właściwość.  
  
### <a name="to-modify-a-system-provided-binding"></a>Aby zmodyfikować powiązania dostarczane przez system  
  
1.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.BasicHttpBinding> klasy i ustaw jej tryb zabezpieczeń na poziomie wiadomości.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Tworzenie niestandardowego powiązania z wiązania i utworzyć <xref:System.ServiceModel.Channels.BindingElementCollection> klasy z jednej z właściwości niestandardowego powiązania.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  W pętli poprzez <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, i jeśli znajdziesz <xref:System.ServiceModel.Channels.HttpTransportBindingElement> klasy, ustaw jego <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwości `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
