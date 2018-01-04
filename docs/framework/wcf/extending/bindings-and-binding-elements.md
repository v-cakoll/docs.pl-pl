---
title: "Powiązania i elementy powiązań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 232d2d23ea88c834d2e28bae99cd2e001f6efac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bindings-and-binding-elements"></a>Powiązania i elementy powiązań
Powiązania są kolekcjami elementów konfiguracji specjalnych, nazywany *elementów wiązania*, które są oceniane przez środowisko wykonawcze usługi zawsze, gdy klient lub punktu końcowego usługi jest tworzona. Typ i kolejność elementów powiązania w powiązaniu Określa wybór i kolejność kanały transportu i protokół punktu końcowego kanału stosu.  
  
 Powiązania, szczególnie dostarczane przez system powiązań, zazwyczaj mają także szereg właściwości konfiguracyjne, które odzwierciedlać najczęściej zmodyfikowane właściwości hermetyzowany elementy.  
  
 Powiązanie musi zawierać dokładnie jeden element powiązania transportu. Każdy element powiązania transportu oznacza komunikat domyślny kodowanie elementu powiązania, która może być zastąpiona przez dodanie co najwyżej jeden element powiązania do powiązania kodowania komunikatu. Oprócz transportu i elementy wiązań kodera powiązania może zawierać dowolną liczbę elementy powiązania protokołu implementujących funkcje niezbędne do usługi i wysyłać wiadomości protokołu SOAP z jeden punkt końcowy do innego. Aby uzyskać więcej informacji, zobacz [za pomocą powiązania do konfigurowania usług i klientów](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozszerzanie powiązań i elementów wiązania  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera powiązania dostarczane przez system, które obejmują szeroki zakres scenariuszy. (Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).) Może to być sytuacji, gdy są potrzebne do utworzenia i użycia powiązania, które nie są uwzględnione w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Następujące scenariusze wymagają utworzenia nowego powiązania.  
  
-   Aby użyć nowego elementu powiązania (na przykład nowy transport, kodowanie lub elementu powiązania protokołu), należy utworzyć nowe powiązanie, który zawiera ten element powiązania. Na przykład jeśli dodano niestandardową `UdpTransportBindingElement` dla transportu UDP, należy utworzyć nowe powiązanie, aby z niego korzystać. Informacje dotyczące wykonywania tego zachowania przy użyciu <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> typu, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
-   Aby skonfigurować istniejące elementy powiązania w taki sposób, który wiązania dostarczane przez system, aby nie pozwala na właściwości publiczne. Na przykład należy utworzyć nowe powiązanie, aby zmienić kolejność, w których podpisywania i szyfrowania są wykonywane operacje. Aby uzyskać informacje dotyczące wykonywania tego zachowania, zobacz [porady: dostosowywanie powiązanie System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
-   Aby ustanowić firmowej standardowe powiązania, które udostępniają tylko opcje konfiguracji określone. Na przykład, aby utworzyć firmy wariant <xref:System.ServiceModel.WSHttpBinding> dla Twojej firmy, w której nie można wyłączyć zabezpieczeń, Utwórz nowe powiązanie, który zachowuje się jak <xref:System.ServiceModel.WSHttpBinding>, ale z zabezpieczeniami zawsze włączone. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
-   Do wykonania niektórych dostosowania metadanych, zwykle, ale niekoniecznie do konfigurowania lub użyj niektórych elementu niestandardowego powiązania. Aby uzyskać więcej informacji na temat zapewnienie obsługi metadanych powiązania i elementy powiązań, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
-  
  
## <a name="channels-bindings-and-binding-elements"></a>Kanały, powiązania i elementy powiązań  
 Powiązania i elementy powiązań są połączenie między modelu programowania aplikacji, który zawiera atrybuty i zachowania, a modelu kanału, który zawiera fabryk i odbiorników, koderów komunikatu i transportu i protokół implementacje. Zazwyczaj elementy wiązania i powiązania są implementowane umożliwiające kanałów, które mają być używane przez warstwy aplikacji.  
  
 Warstwie kanału przekazuje lub odbiera komunikaty z warstwy usług i transporty tych wiadomości między punktami końcowymi. Na komputerze klienckim warstwie kanału jest stos fabryk kanałów, które tworzenia kanałów na punkt końcowy sieci. W usłudze warstwie kanału jest stos odbiorników kanału, akceptujących kanały odebraniu punkt końcowy sieci.  
  
 Istnieją dwa ogólne typy kanałów: protokół kanałów i kanały transportu. Kanały transportu są odpowiedzialne za rzeczywiste transmisję wiadomości z jedną siecią punktu końcowego do innego. Kanały transportu musi mieć kodera wiadomości domyślne i powinno być możliwe do użycia kodera wiadomości alternatywny dostarczonych przez element powiązania kodera wiadomości. Koder komunikatów odpowiada za włączanie <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> do reprezentacji danych przesyłanych w sieci i na odwrót. Kanały protokołów są odpowiedzialne za wdrożenie protokołów SOAP poziomu (na przykład WS-Security lub WS-ReliableMessaging).  
  
 Podstawowy wymóg kanałów transportu i protokołu jest miały zaimplementowane interfejsy wymagane kanału. Aby utworzyć warstwę kanału pracy muszą mieć skojarzone fabryk i odbiorników i tak dalej. Aby użyć implementacji kanału z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musi istnieć elementy skojarzone powiązanie pochodzi od <xref:System.ServiceModel.Channels.BindingElement> dla każdego kanału i powinien być element rozszerzenia powiązania powiązane do włączenia w plikach konfiguracji, które jest pochodną <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jako wspomniano wcześniej, powiązania elementy koderów wiadomości, protokołu i transportu implementacje kanału może być skumulowanych do utworzenia stosu kanału i mechanizmu Aby wyrównać je do zestawu uporządkowanych jest powiązanie. Powiązania i elementy powiązań nawiązać model kanału model programowania aplikacji. Można użyć z implementacji kanału z kodu bezpośrednio, ale chyba że koderów, transportu i protokoły są zaimplementowane jako elementów wiązania nie można użyć z modelu programowania warstwy usługi.  
  
 Aby uzyskać więcej informacji o tworzeniu kanałów i ich elementy wiązania, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
