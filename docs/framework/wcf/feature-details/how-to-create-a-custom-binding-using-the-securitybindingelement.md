---
title: 'Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: da67d923b36d673c87c90ba79b72ad4e1fc64a0c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988753"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement
Windows Communication Foundation (WCF) zawiera kilka powiązań dostarczonych przez system, które można skonfigurować, ale nie zapewniają pełnej elastyczności podczas konfigurowania wszystkich opcji zabezpieczeń obsługiwanych przez funkcję WCF. W tym temacie pokazano, jak utworzyć niestandardowe powiązanie bezpośrednio z poszczególnych elementów powiązania i podświetlić niektóre ustawienia zabezpieczeń, które można określić podczas tworzenia takiego powiązania. Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
> <xref:System.ServiceModel.Channels.SecurityBindingElement>nie obsługuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kształtu kanału, czyli domyślnego kształtu kanału, który jest używany przez transport TCP, gdy <xref:System.ServiceModel.TransferMode> jest ustawiony na <xref:System.ServiceModel.TransferMode.Buffered>. Aby można było <xref:System.ServiceModel.TransferMode> użyć <xref:System.ServiceModel.TransferMode.Streamed> <xref:System.ServiceModel.Channels.SecurityBindingElement> w tym scenariuszu, należy ustawić wartość.  
  
## <a name="creating-a-custom-binding"></a>Tworzenie niestandardowego powiązania  
 W programie WCF wszystkie powiązania składają się z *elementów powiązania*. Każdy element powiązania pochodzi od <xref:System.ServiceModel.Channels.BindingElement> klasy. W przypadku standardowych powiązań dostarczanych przez system elementy powiązania są tworzone i konfigurowane dla Ciebie, chociaż można dostosować niektóre ustawienia właściwości.  
  
 W przeciwieństwie do tworzenia niestandardowego powiązania, elementy powiązania są tworzone i konfigurowane oraz <xref:System.ServiceModel.Channels.CustomBinding> tworzony jest z elementów powiązania.  
  
 W tym celu należy dodać pojedyncze elementy powiązania do kolekcji reprezentowanej przez wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, a następnie `Elements` ustawić właściwość `CustomBinding` równą temu obiektowi. Należy dodać elementy powiązania w następującej kolejności: Przepływ transakcji, Niezawodna sesja, zabezpieczenia, kompozytowe drukowanie dwustronne, jednokierunkowe, zabezpieczenia strumieniowe, kodowanie komunikatów i transport. Należy zauważyć, że nie wszystkie elementy powiązania wymienione w każdym powiązaniu są wymagane.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Trzy elementy powiązań odnoszą się do zabezpieczeń na poziomie komunikatów, z których wszystkie <xref:System.ServiceModel.Channels.SecurityBindingElement> pochodzą z klasy. Trzy <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>i. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Służy do zapewnienia zabezpieczeń w trybie mieszanym. Pozostałe dwa elementy są używane, gdy warstwa komunikatów zapewnia zabezpieczenia.  
  
 Dodatkowe klasy są używane, gdy zapewnione są zabezpieczenia na poziomie transportu:  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Wymagane elementy powiązania  
 Istnieje duża liczba możliwych do powiązania elementów, które można połączyć w powiązanie. Nie wszystkie te kombinacje są prawidłowe. W tej sekcji opisano wymagane elementy, które muszą być obecne w powiązaniu zabezpieczeń.  
  
 Prawidłowe powiązania zabezpieczeń są zależne od wielu czynników, w tym:  
  
- Tryb zabezpieczeń.  
  
- Protokół transportowy.  
  
- Wzorzec wymiany komunikatów (unikatowy MEP) określony w umowie.  
  
 W poniższej tabeli przedstawiono prawidłowe konfiguracje stosu elementów powiązania dla każdej kombinacji powyższych czynników. Należy pamiętać, że są to minimalne wymagania. Można dodać do powiązania dodatkowe elementy powiązania, takie jak elementy powiązania kodowania komunikatów, elementy powiązania transakcji i inne elementy powiązania.  
  
|Tryb zabezpieczeń|Transportu|Wzorzec wymiany komunikatów kontraktu|Wzorzec wymiany komunikatów kontraktu|Wzorzec wymiany komunikatów kontraktu|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transportu|Schemat||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Message|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Tcp|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mieszany (transport z poświadczeniami wiadomości)|Schemat|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|SymmetricSecurityBindingElement (tryb uwierzytelniania = SecureConversation)|  
|||OneWayBindingElement|||  
|||Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|Protokół SSL lub StreamSecurityBindingElement systemu Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Należy pamiętać, że na SecurityBindingElements istnieje wiele konfigurowalnych ustawień. Aby uzyskać więcej informacji, zobacz [elementu SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Aby uzyskać więcej informacji, zobacz [bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Tworzenie niestandardowego powiązania korzystającego z SymmetricSecurityBindingElement  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy o nazwie `outputBec`.  
  
2. Wywołaj metodę `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`statyczną, która zwraca wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.  
  
3. `outputBec` `Add` Dodaj do kolekcji () przez<xref:System.Collections.ObjectModel.Collection%601> wywołanie metody<xref:System.ServiceModel.Channels.BindingElement>klasy. <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
4. Utwórz wystąpienie <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy i Dodaj je do kolekcji (`outputBec`). Określa kodowanie używane przez powiązanie.  
  
5. Utwórz i dodaj go do kolekcji (`outputBec`). <xref:System.ServiceModel.Channels.HttpTransportBindingElement> Oznacza to, że powiązanie korzysta z transportu HTTP.  
  
6. Utwórz nowe niestandardowe powiązanie, tworząc wystąpienie <xref:System.ServiceModel.Channels.CustomBinding> klasy i przekazując kolekcję `outputBec` do konstruktora.  
  
7. Wyniki niestandardowe powiązania mają wiele takich samych cech jak standard <xref:System.ServiceModel.WSHttpBinding>. Określa zabezpieczenia na poziomie wiadomości i poświadczenia systemu Windows, ale wyłącza bezpieczne sesje, wymaga podania poświadczeń usługi poza pasmem i nie szyfruje podpisów. Ostatni można kontrolować tylko przez ustawienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> właściwości, jak pokazano w kroku 4. Pozostałe dwa mogą być kontrolowane przy użyciu ustawień dla standardowego powiązania.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kompletną funkcję do tworzenia niestandardowego powiązania, które używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
