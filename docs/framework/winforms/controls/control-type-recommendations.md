---
title: Zalecenia dotyczące typu formantu
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: fba10de27f7ba6f4c799d2110acd87394b7dbc95
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015996"
---
# <a name="control-type-recommendations"></a>Zalecenia dotyczące typu formantu

.NET Framework umożliwia tworzenie i implementowanie nowych kontrolek. Oprócz znanej kontrolki użytkownika można teraz dowiedzieć się, że można pisać niestandardowe kontrolki, które wykonują własne malowanie, a także możliwość rozszerzenia funkcji istniejących formantów poprzez dziedziczenie. Wybór typu formantu do utworzenia może być mylący. Ta sekcja zawiera informacje o różnicach między różnymi typami formantów, z których można dziedziczyć, i podaje uwagi dotyczące typu do wyboru dla projektu.

> [!NOTE]
> Jeśli chcesz utworzyć formant do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="inheriting-from-a-windows-forms-control"></a>Dziedziczenie z kontrolki Windows Forms

Można utworzyć formant dziedziczony z dowolnej istniejącej kontrolki Windows Forms. Takie podejście pozwala zachować wszystkie nieodłączne funkcje kontrolki Windows Forms, a następnie zwiększyć tę funkcjonalność poprzez dodanie niestandardowych właściwości, metod lub innych funkcji. Na przykład można utworzyć formant pochodny <xref:System.Windows.Forms.TextBox> , który może akceptować tylko cyfry i automatycznie konwertuje dane wejściowe na wartość. Taki formant może zawierać kod weryfikacyjny, który został wywołany za każdym razem, gdy tekst w polu tekstowym został zmieniony, i może mieć dodatkową właściwość, wartość. W niektórych kontrolkach można również dodać niestandardowy wygląd do interfejsu graficznego kontrolki, zastępując <xref:System.Windows.Forms.Control.OnPaint%2A> metodę klasy bazowej.

 Dziedzicz z kontrolki Windows Forms, jeśli:

- Większość potrzebnych funkcji jest już identyczna z istniejącą kontrolką Windows Forms.

- Nie potrzebujesz niestandardowego interfejsu graficznego lub chcesz zaprojektować nowy fronton graficzny dla istniejącej kontrolki.

## <a name="inheriting-from-the-usercontrol-class"></a>Dziedziczenie z klasy UserControl

Kontrolka użytkownika jest kolekcją Windows Forms formantów hermetyzowanych do wspólnego kontenera. Kontener zawiera wszystkie funkcje, które są skojarzone z poszczególnymi kontrolkami Windows Forms i pozwala wybiórczo ujawniać i powiązać ich właściwości. Przykładem kontrolki użytkownika może być kontrolka utworzona w celu wyświetlenia danych o adresie klienta z bazy danych. Ta kontrolka będzie zawierać kilka pól tekstowych do wyświetlania poszczególnych pól i kontrolek przycisków do nawigowania po rekordach. Właściwości powiązania danych mogą być ujawniane selektywnie, a cała kontrola może zostać spakowana i ponownie użyta z aplikacji do aplikacji.

Dziedzicz z klasy <xref:System.Windows.Forms.UserControl> , jeśli:

- Chcesz połączyć funkcje kilku Windows Forms formantów w jedną jednostkę wielokrotnego użytku.

## <a name="inheriting-from-the-control-class"></a>Dziedziczenie z klasy kontrolek

Innym sposobem, aby utworzyć formant, jest utworzenie go znacznie od podstaw przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasa zapewnia wszystkie podstawowe funkcje wymagane przez kontrolki (na przykład zdarzenia), ale nie ma funkcji specyficznych dla kontroli ani interfejsu graficznego. Tworzenie kontrolki przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga dużej liczby myśli i wysiłku niż dziedziczenie z kontrolki użytkownika lub istniejącej kontrolki Windows Forms. Autor musi napisać kod dla <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzenia kontrolki, a także dowolny kod specyficzny dla funkcjonalności, który jest wymagany. Jednak większa elastyczność jest dozwolona i można dostosować kontrolę do własnych potrzeb. Przykładem kontrolki niestandardowej jest kontrolka zegara, która duplikuje wygląd i działanie zegara analogowego. Nastąpi wywołanie niestandardowego rysowania, aby spowodować, że zegar zostanie przesunięty w <xref:System.Windows.Forms.Timer.Tick> odpowiedzi na zdarzenia z wewnętrznego składnika czasomierza.

Dziedzicz z klasy <xref:System.Windows.Forms.Control> , jeśli:

- Chcesz zapewnić niestandardową reprezentację formantu.

- Musisz zaimplementować niestandardowe funkcje, które nie są dostępne za poorednictwem formantów standardowych.

## <a name="related-articles"></a>Pokrewne artykuły:

- [Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [Przewodnik: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)

- [Przewodnik: Dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [Instrukcje: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)

- [Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)

- [Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)

- [Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)

- [Instrukcje: Tworzenie złożonych kontrolek](how-to-author-composite-controls.md)

- [Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)

- [Instrukcje: Utwórz formant Windows Forms, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Opracowywanie prostej kontrolki Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
