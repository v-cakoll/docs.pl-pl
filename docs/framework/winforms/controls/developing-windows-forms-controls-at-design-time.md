---
title: "Opracowywanie formantów formularzy systemu Windows w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4f9680bb64339f2f232793beb9c47a36c07aa4a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Opracowywanie formantów formularzy systemu Windows w czasie projektowania
Dla autorów kontroli programu .NET Framework zapewnia szereg kontroli tworzenia technologii. Autorzy nie są ograniczone do projektowania formanty złożone, które działają jako kolekcja istniejących formantów. Poprzez dziedziczenie możesz utworzyć własne kontrolki z istniejących formantów złożonych lub istniejących formantów formularzy systemu Windows. Można również projektować własne formantach, które implementują niestandardowe malowania. Te opcje umożliwiają dużą elastyczność w projekcie i funkcjonalności interfejsu visual. Aby móc korzystać z tych funkcji, należy zapoznać się z opartej na obiektach pojęcia dotyczące programowania.  
  
> [!NOTE]
>  Nie jest konieczne dogłębnej wiedzy dziedziczenia, ale może być przydatne do odwoływania się do [podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli chcesz tworzyć własne kontrolki formularzy sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Przedstawia sposób tworzenia prostego formantu złożonego w języku Visual Basic.  
  
 [Wskazówki: Tworzenie formantu złożonego za pomocą Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Przedstawia sposób tworzenia prostego formantu złożonego w języku C#.  
  
 [Wskazówki: Dziedziczenie z formantu formularzy systemu Windows za pomocą Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Przedstawia sposób tworzenia prostego formantu formularzy systemu Windows za pomocą dziedziczenia w języku Visual Basic.  
  
 [Wskazówki: Dziedziczenie z formantu formularzy systemu Windows w języku Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Przedstawia sposób tworzenia prostego formantu formularzy systemu Windows za pomocą dziedziczenia w języku C#.  
  
 [Wskazówki: Przeprowadzanie typowych zadań z tagami inteligentnymi na Windows formantów formularzy](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Pokazuje, jak korzystać z funkcji tagów inteligentnych na formanty formularzy systemu Windows.  
  
 [Porady: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Przedstawia sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atrybut do serializacji kolekcji.  
  
 [Wskazówki: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Pokazuje, jak można debugować zachowanie czasu projektowania formantu formularzy systemu Windows.  
  
 [Wskazówki: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Pokazuje, jak ścisła integracja złożonych kontrolek w środowisku projektowania.  
  
 [Porady: formanty autoryzacji dla formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Zawiera omówienie zagadnienia dotyczące formantu formularzy systemu Windows.  
  
 [Porady: autoryzowanie formantów złożonych](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Przedstawia sposób tworzenia formantu przez dziedziczenie z formantu złożonego.  
  
 [Porady: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Zawiera omówienie procedury tworzenia złożonych kontrolek.  
  
 [Porady: dziedziczyć Windows istniejących formantów formularzy](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Przedstawia sposób tworzenia przez dziedziczenie z formantu rozszerzonego <xref:System.Windows.Forms.Button> kontrolować klasy.  
  
 [Porady: dziedziczenie z klasy formantów](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Omówienie Tworzenie formantu rozszerzonego.  
  
 [Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.Control.Dock%2A> wyrównywanie formantu z krawędzią formularza przypada dla właściwości.  
  
 [Porady: wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Zawiera procedury dotyczące instalowania formantu, tak aby był wyświetlany w **Dostosowywanie przybornika** okno dialogowe.  
  
 [Porady: Podaj mapy bitowej przybornika dla formantu](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Przedstawia sposób użycia <xref:System.Drawing.ToolboxBitmapAttribute> do wyświetlenia ikona obok formantu niestandardowego w **przybornika**.  
  
 [Porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Przedstawia sposób użycia **kontenera testu UserControl** do testowania zachowanie formantu złożonego.  
  
 [Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Wyjaśniono znaczenie i korzystanie z listy błędów czasu projektowania, który jest wyświetlany w programie Microsoft Visual Studio, gdy projektant formularzy systemu Windows nie udało się załadować.  
  
 [Rozwiązywanie problemów z formantami oraz autoryzacją](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Pokazuje, jak zdiagnozować i rozwiązać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 W tym artykule omówiono sposób tworzenia Kontrolki niestandardowe z programu .NET Framework.  
  
 [Niezależność od języka i elementy niezależne od języka](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Wprowadza środowisko uruchomieniowe języka wspólnego, której celem jest uproszczenie tworzenia i używania składników. Ważnym aspektem uproszczenie to jest rozszerzone możliwości współdziałania między składnikami napisane przy użyciu różnych języków programowania. Wspólne specyfikacji języka (CLS) pozwala na tworzenie narzędzia i składniki, które współpracują z wielu języków programowania.  
  
 [Wskazówki: Automatyczne zapełnianie przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Opisuje sposób włączania programu składnika lub kontrolki ma być wyświetlany w **Dostosowywanie przybornika** okno dialogowe.
