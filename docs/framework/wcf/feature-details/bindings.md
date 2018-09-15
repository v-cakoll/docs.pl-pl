---
title: Powiązania WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 1930826cf51d67ceb789e20920ca42f04d1adc1b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647385"
---
# <a name="windows-communication-foundation-bindings"></a>Powiązania WCF (Windows Communication Foundation)
Windows Communication Foundation (WCF) oddziela, jak oprogramowania dla aplikacji został napisany, uwzględniając jak ją komunikuje się z innym oprogramowaniem. Powiązania są używane do określenia transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą. WCF używa powiązania do generowania podstawowej reprezentacji przewodowy punktu końcowego, więc większość Szczegóły powiązania uzgadnia przez strony komunikujące się. Najprostszym sposobem osiągnięcia tego jest dla klientów usługi użyto tych samych powiązanie punktu końcowego dla zastosowań usługi. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [za pomocą wiązania, aby skonfigurować Windows Communication Foundation i klientów](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Powiązanie składa się z kolekcji elementów wiązania. Każdy element w tym artykule opisano niektóre aspekty jak punkt końcowy komunikuje się z klientami. Powiązanie musi zawierać co najmniej jeden element powiązania transportu, co najmniej jeden Kodowanie komunikatu element powiązania (który zawiera element powiązania transportu domyślnie) i dowolna liczba innych protokołu elementy powiązania. Proces, który tworzy środowisko uruchomieniowe poza ten opis umożliwia każdy element powiązania współtworzyć kod do tego środowiska uruchomieniowego.  
  
 Usługi WCF zawiera powiązania, które zawierają typowe opcje elementów wiązania. Mogą one być używane z ustawień domyślnych, lub możesz zmodyfikować te wartości domyślne, zgodnie z wymaganiami użytkownika. Te powiązania dostarczane przez system mają właściwości, które umożliwiają bezpośrednią kontrolę nad elementy powiązania i ich ustawienia. Można również łatwo pracować side-by-side z wieloma wersjami powiązanie, dając każdej wersji powiązanie własną nazwę. Aby uzyskać więcej informacji, zobacz [powiązania Configuring System-Provided](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Jeśli potrzebujesz kolekcję elementów wiązania nie podano za pomocą jednej z tych powiązań dostarczanych przez system, można utworzyć niestandardowego powiązania, który zawiera kolekcję elementów wymaganych powiązań. Te powiązania niestandardowego są łatwo tworzyć i czy wymagają nowej klasy, ale nie są oferowane właściwości do kontrolowania elementy powiązania lub ich ustawienia. Można uzyskać dostęp do elementów powiązania i zmieniać ustawienia kolekcji, w którym się znajdują. Aby uzyskać więcej informacji, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 W tym artykule opisano sposób użycia i modyfikować powiązania, udostępnianych przez usługi WCF na potrzeby typowych scenariuszy.  
  
 [Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 W tym artykule opisano sposób definiowania powiązania Windows Communication Foundation (WCF) dla usług i klientów obowiązkowo w kodzie i deklaratywne przy użyciu konfiguracji.  
  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Opisano, czego <xref:System.ServiceModel.Channels.CustomBinding> jest i gdy jest używany.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
