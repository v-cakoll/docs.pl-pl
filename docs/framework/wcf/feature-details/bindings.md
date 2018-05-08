---
title: Powiązania WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 373f7feb64d69373630c942750f264d559643a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communcation-foundation-bindings"></a>Powiązania WCF (Windows Communication Foundation)
Windows Communication Foundation (WCF) oddziela sposób zapisywania oprogramowania dla aplikacji z jak on komunikuje się z innym oprogramowaniem. Powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą. Usługi WCF używa powiązania do generowania danych przesyłanych w sieci podstawowej reprezentację punktu końcowego, dlatego większość szczegóły wiązania należy uzgodnić przez strony komunikujące się. Najprostszym sposobem osiągnąć ten cel jest dla klientów usługi można używać tego samego powiązanie punktu końcowego do zastosowań usługi. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [przy użyciu powiązań, aby skonfigurować usługi systemu Windows Communication Foundation i klientów](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Powiązanie składa się z kolekcji elementów wiązania. Każdy element opisano niektóre aspekty jak punkt końcowy komunikuje się z klientami. Powiązanie musi zawierać co najmniej jeden element powiązania transportu, co najmniej jeden Kodowanie komunikatu element powiązania (co element powiązania transportu może zapewnić domyślnie), a elementy powiązania protokołu wiele innych. Proces, który tworzy moduł wykonawczy poza ten opis umożliwia każdego elementu powiązania do ich współtworzenia kodu do tego środowiska wykonawczego.  
  
 Usługi WCF zawiera powiązań, które zawiera typowe opcje elementów wiązania. Te mogą być używane z ustawień domyślnych, lub zmodyfikować te wartości domyślne, zgodnie z wymaganiami użytkownika. Te powiązania dostarczane przez system ma właściwości, które umożliwia bezpośrednią kontrolę nad elementy wiązania i ich ustawienia. Można również łatwo pracować side-by-side z wieloma wersjami powiązania przez nadanie każdej wersji powiązania własną nazwę. Aby uzyskać więcej informacji, zobacz [powiązania Configuring System-Provided](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Jeśli potrzebujesz kolekcję elementów wiązania nie podano za pomocą jednej z tych powiązań dostarczane przez system, można utworzyć niestandardowego powiązania, który zawiera kolekcję elementów wymaganych powiązań. Te niestandardowe powiązania łatwych do tworzenia i wymagają nowej klasy, ale nie udostępniają właściwości sterujące elementy powiązania lub ich ustawienia. Możesz dostęp do elementów powiązania i zmieniać ustawienia za pomocą kolekcji, który je zawiera. Aby uzyskać więcej informacji, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Opisuje sposób używania i modyfikowania powiązań, które zapewnia usługi WCF do obsługi typowych scenariuszy.  
  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Opisuje sposób zdefiniowania powiązania Windows Communication Foundation (WCF) dla usług i klientów imperatively w kodzie i deklaratywnie za pomocą konfiguracji.  
  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Opisano, co <xref:System.ServiceModel.Channels.CustomBinding> jest i gdy jest używana.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
