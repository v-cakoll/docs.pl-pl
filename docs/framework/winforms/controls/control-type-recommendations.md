---
title: Zalecenia dotyczące typu formantu
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: b2193c862b0bfe0ffbdc55f5d7073409b03a040d
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442948"
---
# <a name="control-type-recommendations"></a>Zalecenia dotyczące typu formantu
Zapewnia .NET Framework power opracowanie i wdrożenie nowych kontrolek. Oprócz kontrolki użytkownika znanych teraz znajdziesz się możliwość zapisywania niestandardowych formantów, które narysowania własne, a nawet mogą rozszerzać funkcjonalność istniejących kontrolek poprzez dziedziczenie. Przy wyborze rozwiązania, jakiego typu formantu, aby utworzyć może być mylące. W tej sekcji przedstawiono różnice między różnymi typami kontrolek, z którego może dziedziczyć i zapewnia uwagi dotyczące wpisz, aby wybrać projekt.  
  
> [!NOTE]
>  Jeśli chcesz utworzyć formant do użycia w formularzach sieci Web, zobacz artykuł [tworzenia formanty serwera ASP.NET niestandardowe](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Dziedziczenie z Windows formantu formularzy  
 Odziedziczoną kontrolkę może pochodzić z dowolnego istniejącego formantu Windows Forms. To podejście pozwala zachować wszystkie funkcje nieprzerwaną pracę formantu Windows Forms i następnie rozszerzyć tę funkcję, dodając niestandardowe właściwości, metody i innych funkcji. Na przykład utworzyć formant pochodzące z <xref:System.Windows.Forms.TextBox> który może akceptować tylko liczby i automatycznie konwertuje dane wejściowe na wartość. Taki formant może zawierać kod sprawdzania poprawności, który został wywołany po każdym zmieniony tekst w polu tekstowym i może mieć dodatkowe właściwości wartości. W niektórych kontrolek, można również dodać niestandardowy wygląd interfejsu graficznego kontrolki poprzez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej.  
  
 Dziedziczenie z kontrolki formularzy Windows Forms, jeśli:  
  
-   Większość funkcji, których potrzebujesz już jest identyczna z istniejącej kontrolki Windows Forms.  
  
-   Nie ma potrzeby niestandardowego interfejsu graficznego lub projektowania nowych graficznych fronton dla istniejącej kontrolki.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dziedziczenie z klasy UserControl  
 Formant użytkownika to zbiór kontrolek formularzy Windows Forms umieszczane na wspólnym kontenerem. Zawiera wszystkie funkcje nieprzerwaną pracę związany z każdą z kontrolek Windows Forms i umożliwia selektywne udostępnianie i wiązania ich właściwości kontenera. Przykładem kontrolki użytkownika może być kontrolki utworzona w celu wyświetlenia danych adres klienta z bazy danych. Ten formant obejmuje kilka pól tekstowych do wyświetlenia każdego pola i formanty przycisków, aby poruszać się po rekordów. Selektywnie widoczne właściwości powiązania danych, a cały kontroli może spakowane i ponownie z aplikacji do aplikacji.  
  
 Dziedzicz <xref:System.Windows.Forms.UserControl> klasy, jeśli:  
  
-   Chcesz połączyć funkcje kilka kontrolek Windows Forms w pojedynczą jednostkę wielokrotnego użytku.  
  
## <a name="inheriting-from-the-control-class"></a>Dziedziczenie z klasy formantów  
 Innym sposobem, aby utworzyć formant jest utworzenie jednego znacznie od podstaw przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasy zawiera wszystkie podstawowe funkcje wymagane przez formanty (na przykład zdarzenia), ale funkcje specyficzne dla formantu lub interfejsu graficznego. Tworzenie formantu przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga o wiele więcej myślenia i nakładu pracy niż dziedziczenie z kontrolki użytkownika lub istniejącej kontrolki Windows Forms. Autor trzeba napisać kod dla <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzenia kontroli, jak również wszelki kod określonych funkcji, który jest potrzebny. Większa elastyczność jest dozwolone, jednak i możesz dostosować niestandardowego formantu do własnych potrzeb dokładnie. Przykład formantu niestandardowego jest formantem zegara powielającą wygląd i działanie zegar analogowy. Malowanie niestandardowe będą wywoływane w celu spowodować ręce zegar przenoszone w odpowiedzi na <xref:System.Windows.Forms.Timer.Tick> zdarzenia ze składnika wewnętrznego zegara.  
  
 Dziedzicz <xref:System.Windows.Forms.Control> klasy, jeśli:  
  
-   Chcesz zapewnić niestandardowy graficzną reprezentację kontrolki.  
  
-   Musisz zaimplementować niestandardowy funkcji, która nie jest dostępna za pośrednictwem standardowych kontrolek.  
  
-   [Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [Przewodnik: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [Instrukcje: Dostarczanie mapy bitowej przybornika dla formantu](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [Instrukcje: Dziedzicz Windows istniejących formantów formularzy](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [Przewodnik: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [Instrukcje: Dziedziczenie z klasy formantów](how-to-inherit-from-the-control-class.md)  
  
-   [Instrukcje: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Instrukcje: Wyrównywanie formantu z krawędziami formularzy w czasie projektowania](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [Instrukcje: Dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [Instrukcje: Tworzenie kontrolek dla formularzy Windows Forms](how-to-author-controls-for-windows-forms.md)  
  
-   [Instrukcje: Formanty złożone autora](how-to-author-composite-controls.md)  
  
-   [Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [Przewodnik: Tworzenie kontrolki formularzy Windows wykorzystującego funkcje czasu projektowania w programie Visual Studio](creating-a-wf-control-design-time-features.md)  
  
-   [Instrukcje: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie kontrolki formularzy Windows prosty](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
