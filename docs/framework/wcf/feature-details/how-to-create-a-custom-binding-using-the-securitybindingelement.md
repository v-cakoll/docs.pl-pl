---
title: 'Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1e288daeb717fa9fa041d552cac4ec5d0cd28808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495635"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement
Windows Communication Foundation (WCF) zawiera kilka powiązania dostarczane przez system, można skonfigurować, które nie udostępniają pełną elastyczność podczas konfigurowania wszystkie opcje zabezpieczeń obsługiwanych przez usługę WCF. W tym temacie przedstawia sposób tworzenia niestandardowego powiązania bezpośrednio z powiązania poszczególnych elementów i zaznacza niektórych ustawień zabezpieczeń, które można określić podczas tworzenia takiego powiązania. Aby uzyskać więcej informacji o tworzeniu niestandardowych powiązań, zobacz [rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> nie obsługuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanału kształtu, który jest używany domyślny kanał kształtu przez TCP podczas transportu <xref:System.ServiceModel.TransferMode> ma ustawioną wartość <xref:System.ServiceModel.TransferMode.Buffered>. Należy ustawić <xref:System.ServiceModel.TransferMode> do <xref:System.ServiceModel.TransferMode.Streamed> aby można było używać <xref:System.ServiceModel.Channels.SecurityBindingElement> w tym scenariuszu.  
  
## <a name="creating-a-custom-binding"></a>Tworzenie niestandardowego powiązania  
 W programie WCF składają się wszystkie powiązania z *elementów wiązania*. Każdy element powiązania jest pochodną <xref:System.ServiceModel.Channels.BindingElement> klasy. Standardowe powiązania dostarczane przez system elementy powiązania są tworzone i skonfigurowany, mimo że można dostosowywać niektóre ustawienia właściwości.  
  
 W przeciwieństwie do tworzenia niestandardowego powiązania, elementy powiązania utworzenia i skonfigurowania i <xref:System.ServiceModel.Channels.CustomBinding> jest tworzona na podstawie elementy wiązania.  
  
 W tym celu należy dodać poszczególne elementy w kolekcji reprezentowany przez wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, a następnie ustaw `Elements` właściwość `CustomBinding` równa tego obiektu. Należy dodać elementy wiązania w następującej kolejności: przepływu transakcji, niezawodnej sesji zabezpieczeń, złożone dupleksowy, jednokierunkowe zabezpieczenia strumienia, kodowanie komunikatu i transportu. Należy pamiętać, że nie wszystkie elementy na liście są wymagane w każdym powiązania.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Trzy elementy powiązania są powiązane z zabezpieczeniami na poziomie wiadomości, które pochodzi od <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Są trzy <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Służy do zapewnienia bezpieczeństwa w trybie mieszanym. Inne elementy są używane podczas warstwy komunikat zawiera zabezpieczeń.  
  
 Dodatkowe klasy są używane, gdy została podana zabezpieczeń na poziomie transportu:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Wymagane elementów wiązania  
 Istnieje wiele elementów możliwe powiązanie, które mogą być połączone w powiązaniu. Nie wszystkie te połączenia są prawidłowe. W tej sekcji opisano wymagane elementy, które muszą być obecne w powiązaniu zabezpieczeń.  
  
 Podmioty zabezpieczeń powiązania zależą od wielu czynników, takich jak następujące:  
  
-   Tryb zabezpieczeń.  
  
-   Transport protokołu.  
  
-   Wymiany komunikatów (MEP) określone w umowie.  
  
 W poniższej tabeli przedstawiono konfiguracje stosu element prawidłowego powiązania dla każdej kombinacji poprzedniego czynników. Należy pamiętać, że są one minimalnych wymagań. Można dodać dodatkowe elementy do powiązanie, takie jak kodowanie elementy wiązania, elementy powiązania transakcji i inne elementy powiązania komunikatu.  
  
|Tryb zabezpieczeń|Transportu|Kontrakt wymiany komunikatów|Kontrakt wymiany komunikatów|Kontrakt wymiany komunikatów|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transportu|Protokół HTTPS||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Komunikat|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mieszane (transportu z poświadczeniami komunikatu)|Protokół HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|Element SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||OneWayBindingElement|||  
|||Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Należy pamiętać, że wiele ustawień można skonfigurować na SecurityBindingElements. Aby uzyskać więcej informacji, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Aby uzyskać więcej informacji, zobacz [Secure konwersacje i sesje Secure](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Aby utworzyć niestandardowego powiązania, który używa element SymmetricSecurityBindingElement  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasa o nazwie `outputBec`.  
  
2.  Wywołanie metody statycznej `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, która zwraca wystąpienie klasy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.  
  
3.  Dodaj <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekcji (`outputBec`) przez wywołanie metody `Add` metody <xref:System.Collections.ObjectModel.Collection%601> z <xref:System.ServiceModel.Channels.BindingElement> klasy.  
  
4.  Utwórz wystąpienie <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy i dodaj go do kolekcji (`outputBec`). Określa kodowanie używane przez powiązanie.  
  
5.  Utwórz <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i dodaj go do kolekcji (`outputBec`). To ustawienie określa, czy powiązanie używa transportu HTTP.  
  
6.  Utwórz nowe powiązanie, niestandardowe przez utworzenie wystąpienia <xref:System.ServiceModel.Channels.CustomBinding> klasy i przekazywanie kolekcji `outputBec` do konstruktora.  
  
7.  Wynikowy niestandardowego powiązania ma wiele cech tego samego wzorca <xref:System.ServiceModel.WSHttpBinding>. Określa zabezpieczenia na poziomie komunikatu i poświadczeń systemu Windows, ale wyłącza bezpiecznej sesji, wymaga poświadczeń usługi określonego poza pasmem, a nie szyfruje podpisów. Ostatniego mogą być kontrolowane tylko przez ustawienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> właściwości, jak pokazano w kroku 4. Pozostałe dwa można kontrolować przy użyciu ustawień na powiązanie standardowe.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono pełną funkcję do tworzenia niestandardowego powiązania, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
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
