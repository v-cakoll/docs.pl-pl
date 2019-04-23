---
title: Wiązania i elementy wiązań
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: 33ebb07e350dbbbdd324b442f52dfb6287322bd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976771"
---
# <a name="bindings-and-binding-elements"></a>Wiązania i elementy wiązań
Powiązania są kolekcjami elementów specjalnej konfiguracji o nazwie *elementów wiązania*, które są oceniane przez środowisko wykonawcze usług zawsze wtedy, gdy klientowi lub punkt końcowy usługi jest budowany. Typ i kolejność elementów powiązania w powiązaniu Określa wybór i kolejność kanały transportu i protokołu w stosie kanał punktu końcowego.  
  
 Powiązania, szczególnie powiązania dostarczane przez system, zwykle również oferują szereg właściwości konfiguracji, które odzwierciedlają najczęściej zmodyfikowane właściwości elementy zhermetyzowany powiązania.  
  
 Powiązanie musi zawierać dokładnie jeden element powiązania transportu. Każdy element powiązania transportu oznacza wiadomość domyślną kodowania element powiązania, który może zostać przesłonięta przez dodanie co najwyżej jeden element powiązania do powiązania kodowania komunikatu. Oprócz transportu i elementy powiązań kodera powiązanie może zawierać dowolną liczbę elementy powiązania protokołu implementujące funkcje potrzebne do usługi i Wyślij komunikat protokołu SOAP z jednym punktem końcowym. Aby uzyskać więcej informacji, zobacz [przy użyciu powiązania do konfigurowania usług i klientów](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozszerzanie powiązań i elementy powiązań  
 Windows Communication Foundation (WCF) zawiera powiązania dostarczane przez system, które obejmują szerokiej gamy scenariuszy. (Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).) Jednak może zdarzyć, jednak jeśli potrzebujesz do tworzenia i używania powiązania, który nie znajduje się w usłudze WCF. Następujące scenariusze wymagają utworzenia nowego powiązania.  
  
-   Aby użyć nowego elementu powiązania (na przykład nowy transport, kodowanie lub element powiązania protokołu), należy utworzyć nowe powiązanie, który zawiera ten element powiązania. Na przykład, jeśli dodano niestandardową `UdpTransportBindingElement` dla transportu UDP, należy utworzyć nowe powiązanie, aby z niego korzystać. Aby uzyskać informacje dotyczące wykonywania tego zachowania przy użyciu <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> typu, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
-   Do skonfigurowania istniejące elementy powiązania w taki sposób, który powiązania dostarczane przez system umożliwiającymi nie publiczny właściwości. Na przykład należy utworzyć nowe powiązanie, aby zmienić kolejność, w której podpisywania i szyfrowania operacje są wykonywane. Aby uzyskać informacje dotyczące wykonywania tego zachowania, zobacz [jak: Dostosuj powiązania dostarczane przez System](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
-   Aby ustanowić firmowych standardowe powiązania, które udostępniają tylko opcje określonej konfiguracji. Na przykład, aby utworzyć w firmie wariant <xref:System.ServiceModel.WSHttpBinding> dla Twojej firmy, w której nie można wyłączyć zabezpieczenia, Utwórz nowe powiązanie, który zachowuje się jak <xref:System.ServiceModel.WSHttpBinding>, dzięki zabezpieczeniom zawsze włączone, ale. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
-   Zazwyczaj przeprowadzić pewne dostosowania metadanych, ale niekoniecznie można konfigurować ani używać pewien element niestandardowego powiązania. Aby uzyskać więcej informacji na temat zapewnienie obsługi metadanych powiązania i elementy powiązań, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanały, powiązania i elementy powiązań  
 Powiązania i elementy powiązań są połączenia między modelu programowania aplikacji, która zawiera atrybuty i zachowania, a model kanału, który obejmuje fabryk i odbiorników, koderów wiadomości i transportu i protokół implementacje. Zazwyczaj elementy powiązania i powiązań są implementowane umożliwiające kanały, który będzie używany przez warstwę aplikacji.  
  
 Warstwy kanału przekazywało lub odbiera komunikaty z warstwy usług i służy do transportu wiadomości między punktami końcowymi. Na komputerze klienckim warstwy kanału jest stos fabryki kanałów, które tworzyć kanały w punkcie końcowym sieci. W usłudze warstwy kanału jest stos odbiorniki kanałów, które akceptują kanały, odbierane w punkcie końcowym sieci.  
  
 Istnieją dwa ogólne typy kanałów: protokół kanałów i kanały transportu. Kanały transportu odpowiadają rzeczywistego transmisji komunikatów z punktu końcowego z jednej sieci do innego. Kanały transportu musi mieć domyślne kodera komunikatów i powinien mieć możliwość użycia koder alternatywne komunikat dostarczane za pośrednictwem element powiązania kodera komunikatów. Koder komunikatów jest odpowiedzialny za włączanie <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> do reprezentacji przewodowy i na odwrót. Kanały protokołów są odpowiedzialni za wdrażanie protokoły poziomu SOAP (na przykład WS-Security lub WS-ReliableMessaging).  
  
 Głównym wymaganiem dla kanały transportu i protokół jest miały zaimplementowane interfejsy wymagane kanału. Aby utworzyć warstwy kanału pracy, musi mieć skojarzone fabryk i odbiorników, i tak dalej. Aby użyć implementacji kanał z usługi WCF, musi istnieć elementy powiązania skojarzonego pochodną <xref:System.ServiceModel.Channels.BindingElement> dla każdego kanału i powinien być element rozszerzenia pokrewne powiązania do włączenia w plikach konfiguracji, która wynika z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jak wspomniano wcześniej, wiążącego elementy na stronie koderów wiadomości, protokół i mechanizm transportu implementacje kanału można stos w celu utworzenia stosu kanał, a mechanizm, aby wyrównać uporządkowany zestaw jest powiązanie. Powiązania i elementy powiązań nawiązać model kanału model programowania aplikacji. Można użyć z implementacji kanał, z kodu bezpośrednio, ale chyba że koderów, transportu i protokoły są implementowane jako elementów wiązania nie można używać z modelu programowania warstwy usługi.  
  
 Aby uzyskać szczegółowe informacje na temat tworzenia kanałów i ich elementy powiązania, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
