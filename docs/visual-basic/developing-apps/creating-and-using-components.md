---
title: "Tworzenie składników i korzystanie z nich w Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 453d341961207dd851136aa47a52759b0841424d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-and-using-components-in-visual-basic"></a>Tworzenie składników i korzystanie z nich w Visual Basic
A *składnika* jest klasa implementująca <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interfejsu lub który pochodzi bezpośrednio lub pośrednio z klasy, która implementuje <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składnik jest obiekt wielokrotnego użytku, mogą prowadzić interakcję z innymi obiektami i zapewnia kontrolę nad zasobów zewnętrznych i obsługi w czasie projektowania.  
  
 Ważna cecha składniki te są designable, co oznacza, że klasa, która jest składnikiem mogą być używane w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] zintegrowane środowisko deweloperskie. Składnik można dodany do przybornika, przeciągnąć i upuszczone na formularzu oraz manipulować na powierzchnię projektu. Należy zauważyć, że podstawowa obsługi w czasie projektowania dla składników jest wbudowana w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; dewelopera składnika nie trzeba wykonywać żadnych dodatkowych działań, aby móc korzystać z podstawową funkcjonalność czasu projektowania.  
  
 A *kontroli* jest podobny do składnika, jak są designable. Jednak formantu udostępnia interfejs użytkownika, gdy składnik nie obsługuje. Formant musi pochodzić z jednego z klasy bazowej: <xref:System.Windows.Forms.Control> lub <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Podczas tworzenia składnika  
 Jeśli klasa będzie używany w projekcie, ale powierzchni (np. formularze systemu Windows lub Projektant formularzy sieci Web) nie ma interfejsu użytkownika, powinna być składnika i implementować <xref:System.ComponentModel.IComponent>, lub pochodzi z klasy, która implementuje bezpośrednio lub pośrednio <xref:System.ComponentModel.IComponent>.  
  
 <xref:System.ComponentModel.Component> i <xref:System.ComponentModel.MarshalByValueComponent> klasy są podstawowych implementacji <xref:System.ComponentModel.IComponent> interfejsu. Główną różnicą między tych klas jest to, że <xref:System.ComponentModel.Component> klasy jest przekazywane przez odwołanie, podczas gdy <xref:System.ComponentModel.IComponent> jest przekazywane przez wartość. Poniższa lista zawiera ogólnych wytycznych dla obiektów implementujących.  
  
-   Jeśli składnik musi być przekazywane przez odwołanie, pochodzi z <xref:System.ComponentModel.Component>.  
  
-   Jeśli składnik musi być organizowany przy użyciu wartości, pochodzi z <xref:System.ComponentModel.MarshalByValueComponent>.  
  
-   Składnik nie może pochodzić z jednego z podstawowych implementacji ze względu na pojedyncze dziedziczenie, należy wdrożyć <xref:System.ComponentModel.IComponent>.  
  
 Aby uzyskać więcej informacji na temat obsługi w czasie projektowania, zobacz [atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) i [rozszerzenie obsługuje czasu projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
## <a name="component-classes"></a>Klasy składników  
 <xref:System.ComponentModel> Przestrzeń nazw zawiera klasy, które są używane do implementowania zachowania czasu wykonywania i czasu projektowania, składników i kontrolek. Ta przestrzeń nazw zawiera klasy podstawowe i interfejsy dla wykonania atrybutów i typy konwerterów, powiązanie z danymi źródeł i licencjonowania składników.  
  
 Podstawowe klasy składników są:  
  
-   <xref:System.ComponentModel.Component>. Podstawowa implementacja dla <xref:System.ComponentModel.IComponent> interfejsu. Ta klasa umożliwia obiektu udostępnianie między aplikacjami.  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>. Podstawowa implementacja dla <xref:System.ComponentModel.IComponent> interfejsu.  
  
-   <xref:System.ComponentModel.Container>. Podstawowa implementacja dla <xref:System.ComponentModel.IContainer> interfejsu. Ta klasa hermetyzuje zero lub więcej składników.  
  
 Niektóre klasy używane do licencjonowania składników są:  
  
-   <xref:System.ComponentModel.License>. Abstrakcyjna klasa podstawowa dla wszystkich licencji. Licencja otrzymuje określonego wystąpienia składnika.  
  
-   <xref:System.ComponentModel.LicenseManager>. Udostępnia właściwości i metody, aby dodać licencję do składnika i zarządzania <xref:System.ComponentModel.LicenseProvider>.  
  
-   <xref:System.ComponentModel.LicenseProvider>. Abstrakcyjna klasa podstawowa dla implementacji dostawcy licencji.  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>. Określa <xref:System.ComponentModel.LicenseProvider> klasy do użycia z klasą.  
  
 Klasy powszechnie używany do opisu i przechowywanie składników.  
  
-   <xref:System.ComponentModel.TypeDescriptor>. Zawiera informacje dotyczące właściwości składnika, takie jak jego atrybuty, właściwości i zdarzeń.  
  
-   <xref:System.ComponentModel.EventDescriptor>. Zawiera informacje o zdarzeniu.  
  
-   <xref:System.ComponentModel.PropertyDescriptor>. Zawiera informacje dotyczące właściwości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasa vs. Składnik programu vs. Formant](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 Definiuje *składnika* i *kontroli*i opisano różnice między nimi i klas.  
  
 [Tworzenie składników](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 Przewodnik Wprowadzenie do składników.  
  
 [Wskazówki dotyczące tworzenia składników](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 Łącza do tematów, które zapewniają instrukcje krok po kroku dla programowania składnika.  
  
 [Klasy składników](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 W tym artykule opisano, co sprawia, że klasa składnik sposoby udostępniania funkcji składnika, kontrolowanie dostępu do składników oraz kontrolowanie tworzenia wystąpienia składnika.  
  
 [Rozwiązywanie problemów z formantami oraz autoryzacją](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Wyjaśniono, jak rozwiązać typowe problemy.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dostęp do obsługi w formularzach systemu Windows w czasie projektowania](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)  
 [Porady: rozszerzanie wygląd i zachowanie formantów w trybie projektowania](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b)  
 [Porady: zainicjować niestandardowych formantów w trybie projektowania](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)
