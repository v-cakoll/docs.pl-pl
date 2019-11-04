---
title: Opracowywanie formantów formularzy systemu Windows w czasie projektowania
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f6afb13a01075d3aa2d101100a0c3bfe31c6ee29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460080"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>Opracowywanie formantów Windows Forms w czasie projektowania

W przypadku autorów kontroli .NET Framework zapewnia mnóstwo technologii tworzenia kontroli. Autorzy nie są już ograniczeni do projektowania kontrolek złożonych, które działają jako kolekcja istniejących kontrolek. Za pomocą dziedziczenia można tworzyć własne kontrolki z istniejących wcześniej kontrolek złożonych lub wcześniej istniejących kontrolek Windows Forms. Możesz również projektować własne kontrolki implementujące niestandardowe malowanie. Te opcje umożliwiają znaczną elastyczność projektowania i funkcjonalności interfejsu wizualizacji. Aby skorzystać z tych funkcji, należy zapoznać się z pojęciami programistycznymi opartymi na obiektach.

> [!NOTE]
> Nie jest konieczne dokładne zrozumienie dziedziczenia, ale może się okazać, że warto odnieść się do podstawowych informacji dotyczących [dziedziczenia (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

Jeśli chcesz utworzyć niestandardowe kontrolki do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie złożonego formantu](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\
Pokazuje, jak utworzyć prosty formant złożony w C#.

[Przewodnik: dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
Pokazuje, jak utworzyć prostą kontrolkę Windows Forms przy użyciu C#dziedziczenia w programie.

[Przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
Pokazuje, jak używać funkcji tagów inteligentnych w kontrolkach Windows Forms.

[Przewodnik: Serializowanie kolekcji typów standardowych przy użyciu\ za pomocą DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)
Pokazuje, w jaki sposób używać atrybutu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> do serializacji kolekcji.

[Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
Pokazuje, jak debugować zachowanie formantu Windows Forms w czasie projektowania.

[Przewodnik: Tworzenie formantu Windows Forms, który korzysta z funkcji czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)\
Pokazuje ścisłą integrację złożonego formantu ze środowiskiem projektowym.

[Instrukcje: Tworzenie formantów dla Windows Forms](how-to-author-controls-for-windows-forms.md)\
Zawiera omówienie zagadnień związanych z implementacją kontrolki Windows Forms.

[Instrukcje: Tworzenie kontrolek złożonych](how-to-author-composite-controls.md)\
Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.

[Instrukcje: dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)\
Zawiera przegląd procedury tworzenia złożonego formantu.

[Instrukcje: dziedziczenie z istniejących formantów Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)\
Pokazuje, jak utworzyć formant rozszerzony przez dziedziczenie z klasy kontrolki <xref:System.Windows.Forms.Button>.

[Instrukcje: dziedziczenie z klasy kontrolki](how-to-inherit-from-the-control-class.md)\
Zawiera omówienie tworzenia rozszerzonej kontroli.

[Instrukcje: wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
Pokazuje, w jaki sposób używać właściwości <xref:System.Windows.Forms.Control.Dock%2A>, aby wyrównać formant do krawędzi formularza, który zadziała.

[Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
Pokazuje procedurę instalowania kontrolki tak, aby była widoczna w oknie dialogowym **Dostosowywanie przybornika** .

[Instrukcje: udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
Pokazuje, w jaki sposób używać <xref:System.Drawing.ToolboxBitmapAttribute> do wyświetlania ikony obok kontrolki niestandardowej w **przyborniku**.

[Instrukcje: testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
Pokazuje, jak używać obiektu **UserControl Test Container** do testowania zachowania złożonego formantu.

[Błędy czasu projektowania w Projektant formularzy systemu Windows](design-time-errors-in-the-windows-forms-designer.md)\
Wyjaśnia znaczenie i użycie Lista błędów czasu projektowania, które pojawiają się w Microsoft Visual Studio w przypadku niepowodzenia załadowania projektanta Windows Forms.

[Kontrola rozwiązywania problemów i\ tworzenia składników](troubleshooting-control-and-component-authoring.md)
Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.

## <a name="reference"></a>Tematy pomocy

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>Sekcje pokrewne

[Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)\
W tym artykule omówiono sposób tworzenia własnych niestandardowych kontrolek przy użyciu .NET Framework.

[Niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md)\
Wprowadza środowisko uruchomieniowe języka wspólnego, które jest przeznaczone do uproszczenia tworzenia i używania składników. Ważnym aspektem tego uproszczenia jest ulepszona współpraca między składnikami zapisanymi przy użyciu różnych języków programowania. Common Language Specification (CLS) umożliwia tworzenie narzędzi i składników, które współpracują z wieloma językami programowania.

[Przewodnik: automatyczne zapełnianie przybornika składnikami Niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
Opisuje sposób włączania wyświetlania składnika lub kontrolki w oknie dialogowym **Dostosowywanie przybornika** .
