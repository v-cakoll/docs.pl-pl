---
title: Tworzenie składników i korzystanie z nich w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: ca336e2ffa3831167088d92bfca017ce2226d8a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014326"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Tworzenie składników i korzystanie z nich w Visual Basic
A *składnika* to klasa, która implementuje <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interfejsu, lub który pochodzi bezpośrednio lub pośrednio z klasy, która implementuje <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składnik to obiekt wielokrotnego użytku, mogą wchodzić w interakcje z innymi obiektami i zapewnia kontrolę nad zasobami zewnętrznymi i obsługi w czasie projektowania.  
  
 Ważną funkcją składniki te są designable, co oznacza, że klasa, która jest składnikiem mogą być używane w zintegrowanym środowisku projektowym Visual Studio. Składnik może dodany do przybornika, przeciągnąć i upuszczone na formularzu i zmieniane na powierzchni projektowej. Należy zauważyć, że podstawowa obsługi w czasie projektowania dotyczące składników ma wbudowaną [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; deweloperem składnika nie trzeba wykonywać żadnych dodatkowych działań, aby móc korzystać z podstawowe funkcje czasu projektowania.  
  
 A *kontroli* jest podobne do składnika, ponieważ oba są designable. Formant zapewnia jednak interfejsu użytkownika, a nie składnika. Formant muszą pochodzić z jednej klasy bazowej: <xref:System.Windows.Forms.Control> lub <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Podczas tworzenia składnika  
 Jeśli klasa będzie używana w projekcie, ale powierzchni (np. Windows Forms lub Projektant formularzy sieci Web) nie ma interfejsu użytkownika, należy składnikiem i zaimplementować <xref:System.ComponentModel.IComponent>, lub pochodzić od klasy, która implementuje bezpośrednio lub pośrednio <xref:System.ComponentModel.IComponent>.  
  
 <xref:System.ComponentModel.Component> i <xref:System.ComponentModel.MarshalByValueComponent> klasy stanowią podstawowe implementacje <xref:System.ComponentModel.IComponent> interfejsu. Główną różnicą między tymi klasami. jest to, że <xref:System.ComponentModel.Component> klasy jest przekazywany przez odwołanie, podczas gdy <xref:System.ComponentModel.IComponent> jest przekazywany przez wartość. Poniższa lista zawiera szeroką wytyczne dotyczące implementacji.  
  
- Jeśli składnik musi być przekazywane przez odwołanie, pochodzi od <xref:System.ComponentModel.Component>.  
  
- Jeśli składnik musi być przekazywane przez wartość, pochodzi od <xref:System.ComponentModel.MarshalByValueComponent>.  
  
- Jeśli składnik nie może pochodzić z jednej z implementacji podstawowego ze względu na pojedyncze dziedziczenie, zaimplementować <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Klasy składników  
 <xref:System.ComponentModel> Przestrzeń nazw zawiera klasy, które są używane, aby zaimplementować to zachowanie w czasie wykonywania oraz w czasie projektowania składników i formantów. Ta przestrzeń nazw zawiera klasy podstawowe i interfejsy do implementacji atrybutów i typy konwerterów, powiązanie z danymi źródeł i licencjonowanie składników.  
  
 Klasy składników podstawowych są:  
  
- <xref:System.ComponentModel.Component>. Podstawowa implementacja dla <xref:System.ComponentModel.IComponent> interfejsu. Ta klasa umożliwia obiektu udostępniać między aplikacjami.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. Podstawowa implementacja dla <xref:System.ComponentModel.IComponent> interfejsu.  
  
- <xref:System.ComponentModel.Container>. Podstawowa implementacja dla <xref:System.ComponentModel.IContainer> interfejsu. Ta klasa hermetyzuje zero lub więcej składników.  
  
 Niektóre klasy używane w przypadku licencjonowania składników to:  
  
- <xref:System.ComponentModel.License>. Abstrakcyjna klasa bazowa dla wszystkich licencji. Licencja zostanie ustanowione określonego wystąpienia składnika.  
  
- <xref:System.ComponentModel.LicenseManager>. Udostępnia właściwości i metody umożliwiają dodanie licencji do składnika oraz do zarządzania <xref:System.ComponentModel.LicenseProvider>.  
  
- <xref:System.ComponentModel.LicenseProvider>. Abstrakcyjna klasa bazowa dla implementacji dostawcy licencji.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. Określa <xref:System.ComponentModel.LicenseProvider> klasy za pomocą klasy.  
  
 Klasy często używane do opisywania i przechowywanie składników.  
  
- <xref:System.ComponentModel.TypeDescriptor>. Zawiera informacje o właściwości dla komponentu, takie jak jego atrybuty, właściwości i zdarzenia.  
  
- <xref:System.ComponentModel.EventDescriptor>. Zawiera informacje o zdarzeniu.  
  
- <xref:System.ComponentModel.PropertyDescriptor>. Zawiera informacje dotyczące właściwości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Wyjaśnia, jak rozwiązać typowe problemy.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostęp do obsługi w czasie projektowania w formularzach Windows Forms](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
