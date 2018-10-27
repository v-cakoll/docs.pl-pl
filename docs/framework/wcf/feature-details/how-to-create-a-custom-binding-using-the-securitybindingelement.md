---
title: 'Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: df40d8dbd5af9acf9e9484ee7694df2bba7ad9f1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181137"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement
Windows Communication Foundation (WCF) obejmuje kilka powiązania dostarczane przez system, które można skonfigurować, ale nie zapewniają pełną elastyczność podczas konfigurowania wszystkich opcji zabezpieczeń, które obsługuje usługi WCF. W tym temacie pokazano, jak utworzyć niestandardowego powiązania bezpośrednio z poziomu powiązania poszczególnych elementów i opisano niektóre ustawienia zabezpieczeń, które można określić podczas tworzenia takiego powiązania. Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> nie obsługuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanału kształtu, który jest używany domyślny kanał kształt przez TCP podczas transportu <xref:System.ServiceModel.TransferMode> ustawiono <xref:System.ServiceModel.TransferMode.Buffered>. Należy ustawić <xref:System.ServiceModel.TransferMode> do <xref:System.ServiceModel.TransferMode.Streamed> aby można było używać <xref:System.ServiceModel.Channels.SecurityBindingElement> w tym scenariuszu.  
  
## <a name="creating-a-custom-binding"></a>Tworzenie powiązania niestandardowego  
 W programie WCF składają się wszystkie powiązania z *elementów wiązania*. Każdy element powiązania jest pochodną <xref:System.ServiceModel.Channels.BindingElement> klasy. Standardowa powiązania dostarczane przez system elementy powiązania są tworzone i konfigurowane dla Ciebie, mimo że można dostosowywać niektóre ustawienia właściwości.  
  
 W przeciwieństwie do tworzenia niestandardowego powiązania, elementy powiązania są tworzone i konfigurowane i <xref:System.ServiceModel.Channels.CustomBinding> jest tworzona na podstawie elementy wiązania.  
  
 Aby to zrobić, Dodaj elementy powiązania poszczególnych kolekcji reprezentowany przez wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, a następnie ustaw `Elements` właściwość `CustomBinding` taki sam jak ten obiekt. Należy dodać elementy powiązania w następującej kolejności: przepływu transakcji, niezawodnej sesji, zabezpieczeń, złożonego dwukierunkowego, jednokierunkowe Stream zabezpieczeń, kodowania wiadomości i transportu. Należy zauważyć, że nie wszystkie elementy na liście są wymagane w każde powiązanie.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Trzy elementy powiązania odnoszą się do komunikatu zabezpieczenia na poziomie, z których pochodzi od <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Są trzy <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Służy do zapewnienia bezpieczeństwa w trybie mieszanym. Inne elementy są używane, gdy warstwa komunikatów gwarantuje bezpieczeństwo.  
  
 Dodatkowe klasy są używane, gdy została podana zabezpieczeń na poziomie transportu:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Wymagane elementów wiązania  
 Istnieją dużą liczbę elementów możliwe powiązanie, które mogą być połączone w powiązaniu. Nie wszystkie te kombinacje są prawidłowe. W tej sekcji opisano wymagane elementy, które muszą być obecne w powiązaniu zabezpieczeń.  
  
 Nieprawidłowy zabezpieczeń powiązania zależą od wielu czynników, w tym następujące:  
  
-   Tryb zabezpieczeń.  
  
-   Protokół transportowy.  
  
-   Wymiany komunikatów (MEP) określone w umowie.  
  
 W poniższej tabeli przedstawiono konfiguracje prawidłowego powiązania elementu stosu dla każdej kombinacji poprzedniego czynników. Należy pamiętać, że są one minimalnych wymagań. Możesz dodać dodatkowe elementy do powiązania, np. komunikat o kodowanie elementy wiązania, elementy powiązania transakcji i inne elementy wiązania.  
  
|Tryb zabezpieczeń|Transportu|Wymiany komunikatów kontraktu|Wymiany komunikatów kontraktu|Wymiany komunikatów kontraktu|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transportu|Protokół HTTPS||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||Protokół SSL lub Windows StreamSecurityBindingElement|Protokół SSL lub Windows StreamSecurityBindingElement|Protokół SSL lub Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Komunikat|http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = mechanizmu SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = mechanizmu SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mieszany (transportu z poświadczeniami komunikatu)|Protokół HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = mechanizmu SecureConversation)|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = mechanizmu SecureConversation)|  
|||OneWayBindingElement|||  
|||Protokół SSL lub Windows StreamSecurityBindingElement|Protokół SSL lub Windows StreamSecurityBindingElement|Protokół SSL lub Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Należy zauważyć, że istnieje wiele konfigurowalnych ustawień na SecurityBindingElements. Aby uzyskać więcej informacji, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Aby uzyskać więcej informacji, zobacz [Secure rozmowy i zabezpieczanie sesji](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Aby utworzyć niestandardowego powiązania, który używa element SymmetricSecurityBindingElement  
  
1.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.Channels.BindingElementCollection> klasy o nazwie `outputBec`.  
  
2.  Wywołanie metody statycznej `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, która zwraca wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.  
  
3.  Dodaj <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekcji (`outputBec`) przez wywołanie metody `Add` metody <xref:System.Collections.ObjectModel.Collection%601> z <xref:System.ServiceModel.Channels.BindingElement> klasy.  
  
4.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy i dodać go do kolekcji (`outputBec`). Określa kodowanie używanym przez wiązanie.  
  
5.  Tworzenie <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i dodaj go do kolekcji (`outputBec`). To ustawienie określa, że powiązanie korzysta z protokołu HTTP.  
  
6.  Tworzenie nowego niestandardowego powiązania, tworząc wystąpienie <xref:System.ServiceModel.Channels.CustomBinding> klasy i przekazywanie kolekcji `outputBec` do konstruktora.  
  
7.  Wynikowy niestandardowego powiązania udostępnia wiele takie same charakterystyki jak standardowy <xref:System.ServiceModel.WSHttpBinding>. Określa zabezpieczenia na poziomie komunikatu i poświadczenia Windows, ale wyłącza bezpiecznych sesji, wymaga poświadczeń usługi określonego poza pasmem, a nie szyfruje podpisów. Ostatni mogą być kontrolowane tylko przez ustawienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> właściwości, jak pokazano w kroku 4. Pozostałe dwa można sterować przy użyciu ustawień w powiązaniu standardowych.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono pełny funkcja tworzenia niestandardowego powiązania, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
