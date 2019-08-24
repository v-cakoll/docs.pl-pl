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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eebca72b8c564e6d846eba69b6b59139754738e
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015979"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>Opracowywanie formantów Windows Forms w czasie projektowania

W przypadku autorów kontroli .NET Framework zapewnia mnóstwo technologii tworzenia kontroli. Autorzy nie są już ograniczeni do projektowania kontrolek złożonych, które działają jako kolekcja istniejących kontrolek. Za pomocą dziedziczenia można tworzyć własne kontrolki z istniejących wcześniej kontrolek złożonych lub wcześniej istniejących kontrolek Windows Forms. Możesz również projektować własne kontrolki implementujące niestandardowe malowanie. Te opcje umożliwiają znaczną elastyczność projektowania i funkcjonalności interfejsu wizualizacji. Aby skorzystać z tych funkcji, należy zapoznać się z pojęciami programistycznymi opartymi na obiektach.

> [!NOTE]
> Nie jest konieczne dokładne zrozumienie dziedziczenia, ale może się okazać, że warto odnieść się do podstawowych informacji dotyczących [dziedziczenia (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

Jeśli chcesz utworzyć niestandardowe kontrolki do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\
Pokazuje, jak utworzyć prosty formant złożony w C#.

[Przewodnik: Dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
Pokazuje, jak utworzyć prostą kontrolkę Windows Forms przy użyciu C#dziedziczenia w programie.

[Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
Pokazuje, jak używać funkcji tagów inteligentnych w kontrolkach Windows Forms.

[Przewodnik: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)\
Pokazuje, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> jak używać atrybutu do serializacji kolekcji.

[Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
Pokazuje, jak debugować zachowanie formantu Windows Forms w czasie projektowania.

[Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)\
Pokazuje ścisłą integrację złożonego formantu ze środowiskiem projektowym.

[Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)\
Zawiera omówienie zagadnień związanych z implementacją kontrolki Windows Forms.

[Instrukcje: Tworzenie złożonych kontrolek](how-to-author-composite-controls.md)\
Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.

[Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)\
Zawiera przegląd procedury tworzenia złożonego formantu.

[Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)\
Pokazuje, jak utworzyć formant rozszerzony przez dziedziczenie z <xref:System.Windows.Forms.Button> klasy kontrolek.

[Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)\
Zawiera omówienie tworzenia rozszerzonej kontroli.

[Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
Pokazuje, w jaki sposób <xref:System.Windows.Forms.Control.Dock%2A> używać właściwości, aby wyrównać formant do krawędzi formularza, który on zajmowan.

[Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
Pokazuje procedurę instalowania kontrolki tak, aby była widoczna w oknie dialogowym **Dostosowywanie przybornika** .

[Instrukcje: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
Pokazuje, <xref:System.Drawing.ToolboxBitmapAttribute> jak używać do wyświetlania ikony obok kontrolki niestandardowej w **przyborniku**.

[Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
Pokazuje, jak używać obiektu **UserControl Test Container** do testowania zachowania złożonego formantu.

[Błędy czasu projektowania w Projektant formularzy systemu Windows](design-time-errors-in-the-windows-forms-designer.md)\
Wyjaśnia znaczenie i użycie Lista błędów czasu projektowania, które pojawiają się w Microsoft Visual Studio w przypadku niepowodzenia załadowania projektanta Windows Forms.

[Kontrola i Tworzenie składników rozwiązywania problemów](troubleshooting-control-and-component-authoring.md)\
Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.

## <a name="reference"></a>Tematy pomocy

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>Sekcje pokrewne

[Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)\
W tym artykule omówiono sposób tworzenia własnych niestandardowych kontrolek przy użyciu .NET Framework.

[Niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md)\
Wprowadza środowisko uruchomieniowe języka wspólnego, które jest przeznaczone do uproszczenia tworzenia i używania składników. Ważnym aspektem tego uproszczenia jest ulepszona współpraca między składnikami zapisanymi przy użyciu różnych języków programowania. Common Language Specification (CLS) umożliwia tworzenie narzędzi i składników, które współpracują z wieloma językami programowania.

[Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
Opisuje sposób włączania wyświetlania składnika lub kontrolki w oknie dialogowym **Dostosowywanie przybornika** .
