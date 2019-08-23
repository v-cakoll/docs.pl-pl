---
title: Wiązania WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e7071d56c8dc4b953c4b6349660ca4a8a1b7d23e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952630"
---
# <a name="windows-communication-foundation-bindings"></a>Wiązania WCF (Windows Communication Foundation)
Windows Communication Foundation (WCF) oddziela, w jaki sposób oprogramowanie aplikacji jest zapisywana z tego, jak komunikuje się z innym oprogramowaniem. Powiązania są używane do określania informacji o transportach, kodowaniu i protokole wymaganych przez klientów i usługi do komunikowania się ze sobą. Funkcja WCF używa powiązań do generowania wewnętrznej reprezentacji punktu końcowego, dlatego większość szczegółowych informacji o powiązaniach musi być uzgodniona przez strony, które komunikują się. Najprostszym sposobem osiągnięcia tej wartości jest to, że klienci usługi mogą używać tego samego powiązania, które jest używane przez punkt końcowy usługi. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [using bindings to configure Services and clients](../using-bindings-to-configure-services-and-clients.md).  
  
 Powiązanie składa się z kolekcji elementów powiązania. Każdy element opisuje pewne aspekty, w jaki punkt końcowy komunikuje się z klientami. Powiązanie musi zawierać co najmniej jeden element powiązania transportu, co najmniej jeden element powiązania kodowania komunikatów (który może być udostępniany przez element powiązania transportu domyślnie) i dowolną liczbę innych elementów powiązania protokołu. Proces, który kompiluje środowisko uruchomieniowe z tego opisu, umożliwia każdemu elementowi powiązania, aby współtworzyć kod w tym środowisku uruchomieniowym.  
  
 Funkcja WCF oferuje powiązania zawierające typowe wybory elementów powiązania. Mogą one być używane z domyślnymi ustawieniami lub można modyfikować te wartości domyślne zgodnie z wymaganiami użytkownika. Te powiązania dostarczone przez system mają właściwości, które umożliwiają bezpośrednią kontrolę nad elementami powiązania i ich ustawieniami. Możesz również łatwo współpracować z wieloma wersjami powiązań, nadając każdej wersji powiązania swoją własną nazwę. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie powiązań dostarczonych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Jeśli potrzebujesz kolekcji elementów powiązania niedostarczonych przez jedno z tych powiązań dostarczonych przez system, możesz utworzyć niestandardowe powiązanie, które składa się z kolekcji wymaganych elementów powiązania. Te niestandardowe powiązania są łatwe do utworzenia i nie wymagają nowej klasy, ale nie zapewniają właściwości do kontrolowania elementów powiązania ani ich ustawień. Możesz uzyskać dostęp do elementów powiązania i zmodyfikować ich ustawienia za pomocą kolekcji, która je zawiera. Aby uzyskać szczegółowe informacje, zobacz [niestandardowe powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Opisuje, jak używać i modyfikować powiązania zapewniane przez WCF do obsługi typowych scenariuszy.  
  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 Zawiera opis sposobu definiowania powiązań Windows Communication Foundation (WCF) dla usług i klientów w sposób niezbędny w kodzie i deklaratywnie korzystających z konfiguracji.  
  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Opisuje, co <xref:System.ServiceModel.Channels.CustomBinding> to jest i kiedy jest używany.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
