---
title: Wiązania i elementy wiązań
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: d4d69495c1ae19b6799fdb9981f6b332cc2580d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795850"
---
# <a name="bindings-and-binding-elements"></a>Wiązania i elementy wiązań
Powiązania są kolekcjami specjalnych elementów konfiguracji nazywanymi *elementami powiązania*, które są oceniane przez środowisko uruchomieniowe usługi za każdym razem, gdy jest konstruowany klient lub punkt końcowy usługi. Typ i porządek elementów powiązania w ramach powiązania określa kolejność zaznaczania i układania kanałów protokołu i transportu w stosie kanału punktu końcowego.  
  
 Powiązania, w szczególności powiązania dostarczone z systemem, zazwyczaj również mają kilka właściwości konfiguracji, które odzwierciedlają najczęściej modyfikowane właściwości elementów z hermetyzowanymi powiązaniami.  
  
 Powiązanie musi zawierać dokładnie jeden element powiązania transportu. Każdy element powiązania transportu oznacza domyślny element powiązania kodowania komunikatów, który może zostać przesłonięty przez dodanie maksymalnie jednego elementu powiązania kodowania komunikatów do powiązania. Oprócz elementów powiązania transportu i kodera powiązanie może zawierać dowolną liczbę elementów powiązania protokołów, które razem implementują funkcje potrzebne do obsługi i wysyłania komunikatu protokołu SOAP z jednego punktu końcowego do innego. Aby uzyskać szczegółowe informacje, zobacz [using bindings to configure Services and clients](../using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozszerzanie powiązań i elementów powiązania  
 Windows Communication Foundation (WCF) obejmuje powiązania dostarczone przez system, które obejmują szeroką gamę scenariuszy. (Aby uzyskać więcej informacji, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md)). Mogą jednak wystąpić sytuacje, w których konieczne jest utworzenie i użycie powiązania, które nie jest zawarte w programie WCF. Poniższe scenariusze wymagają utworzenia nowego powiązania.  
  
- Aby użyć nowego elementu powiązania (takiego jak nowy transport, kodowanie lub element powiązania protokołów), należy utworzyć nowe powiązanie, które zawiera ten element powiązania. Na przykład, jeśli dodano niestandardowe `UdpTransportBindingElement` dla transportu UDP, należy utworzyć nowe powiązanie, aby można było z niego korzystać. Informacje o wykonywaniu tego zachowania przy użyciu <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> typu znajdują się w temacie [Custom bindings](custom-bindings.md).  
  
- W celu skonfigurowania istniejących elementów powiązania w taki sposób, że powiązania dostarczone przez system nie ujawniają właściwości publicznych. Na przykład należy utworzyć nowe powiązanie, aby zmienić kolejność wykonywania operacji podpisywania i szyfrowania. Informacje o wykonywaniu tego zachowania można znaleźć [w temacie How to: Dostosuj powiązanie](how-to-customize-a-system-provided-binding.md)dostarczone przez system.  
  
- Aby ustanowić standardowe powiązania firmowe, które uwidaczniają tylko konkretne opcje konfiguracji. Na przykład, aby utworzyć dla swojej firmy odmianę <xref:System.ServiceModel.WSHttpBinding> dla firmy, w której nie można wyłączyć zabezpieczeń, Utwórz nowe powiązanie, które zachowuje się <xref:System.ServiceModel.WSHttpBinding>jak, ale z zabezpieczeniami zawsze włączone. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md).  
  
- Do wykonywania niektórych dostosowań metadanych, zwykle ale niekoniecznie do konfigurowania lub używania niestandardowego elementu powiązania. Aby uzyskać więcej informacji o dostarczaniu obsługi metadanych do powiązań i elementów powiązań, zobacz temat [Obsługa konfiguracji i metadanych](configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanały, powiązania i elementy powiązania  
 Powiązania i elementy powiązania są połączeniem między modelem programowania aplikacji, który obejmuje atrybuty i zachowania oraz model kanału, który obejmuje fabryki i detektory, kodery komunikatów oraz transport i protokół. metod. Zazwyczaj elementy powiązania i powiązania są implementowane, aby umożliwić używanie kanałów przez warstwę aplikacji.  
  
 Kanał jest wyłączany lub odbierany z warstwy usługi i transportuje te komunikaty między punktami końcowymi. Na kliencie Warstwa kanału to stos fabryk kanałów, które tworzą kanały do punktu końcowego sieci. W przypadku usługi Warstwa kanału to stos odbiorników kanałów, który akceptuje kanały odebrane w punkcie końcowym sieci.  
  
 Istnieją dwa ogólne typy kanałów: kanały protokołu i kanały transportu. Kanały transportu są odpowiedzialne za faktyczną transmisję komunikatu z jednego punktu końcowego sieci do innego. Kanały transportu muszą mieć domyślny koder komunikatów i powinien być w stanie używać alternatywnego kodera komunikatów dostarczonego za pomocą elementu powiązania kodera komunikatów. Koder komunikatów jest odpowiedzialny za przekształcenie <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> w sieci szkieletowej i na odwrót. Kanały protokołu są odpowiedzialne za implementację protokołów na poziomie protokołu SOAP (na przykład WS-Security lub WS-ReliableMessaging).  
  
 Podstawowym wymaganiem dotyczącym transportu i kanałów protokołu jest zaimplementowanie przez nich wymaganych interfejsów kanałów. Aby utworzyć warstwę kanału roboczego, muszą mieć skojarzone fabryki i odbiorniki itd. Aby można było używać implementacji kanału z programu WCF, musi istnieć skojarzone elementy powiązania pochodzące z <xref:System.ServiceModel.Channels.BindingElement> dla każdego kanału i powinien istnieć powiązany element rozszerzenia powiązania do dołączenia do plików konfiguracji, które pochodzą z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jak wspomniano wcześniej, elementy powiązania dla koderów komunikatów, protokołów i implementacji kanału transportowego mogą być ułożone w taki sposób, aby utworzyć stos kanału i mechanizm, aby wyrównać je do zestawu uporządkowanego. Powiązania i elementy powiązań łączą model programowania aplikacji z modelem kanału. Możesz użyć implementacji kanału bezpośrednio z kodu, ale jeśli kodery, transporty i protokoły nie są zaimplementowane jako elementy powiązania, nie mogą być używane z modelu programowania warstw usług.  
  
 Aby uzyskać szczegółowe informacje na temat tworzenia kanałów i ich elementów powiązań, zobacz [Rozszerzanie warstwy kanału](extending-the-channel-layer.md).
