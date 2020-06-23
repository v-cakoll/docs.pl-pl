---
title: Skalowanie automatyczne
description: Dowiedz się, w jaki sposób automatyczne skalowanie umożliwia wyświetlanie formularzy i ich kontrolek, które są przeznaczone do wyświetlania odpowiednio na innej maszynie.
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 93d6b9097c85d7fa7ca88b405ee3d3654e51304b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903691"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatyczne skalowanie w Windows Forms

Automatyczne skalowanie umożliwia formularz i jego kontrolki, zaprojektowane na jednej maszynie z określoną rozdzielczością ekranu lub czcionką systemową, do wyświetlania odpowiednio na innym komputerze z inną rozdzielczością ekranu lub czcionką systemu. Gwarantuje to, że formularz i jego kontrolki będą inteligentnej zmiany rozmiaru, aby były spójne z natywnymi oknami i innymi aplikacjami na maszynach użytkowników i innych deweloperów. Obsługa .NET Framework na potrzeby automatycznego skalowania i stylów wizualnych umożliwia aplikacjom .NET Framework zachowanie spójnego wyglądu i działania w porównaniu do natywnych aplikacji systemu Windows na komputerach poszczególnych użytkowników.

W większości przypadków automatyczne skalowanie działa zgodnie z oczekiwaniami w .NET Framework w wersji 2,0 i nowszych. Jednak zmiany schematu czcionek mogą być problematyczne. Aby zapoznać się z przykładem sposobu rozwiązania tego problemu, zobacz [How to: Rereagowanie na zmiany schematu czcionek w aplikacji Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Potrzeba automatycznego skalowania

Bez automatycznego skalowania aplikacja zaprojektowana dla jednej rozdzielczości ekranu lub czcionki będzie wyświetlana za mała lub zbyt duża, gdy ta rozdzielczość lub czcionka zostanie zmieniona. Na przykład, jeśli aplikacja jest zaprojektowana przy użyciu opcji Tahoma 9 Point jako linia bazowa, bez dostosowania będzie wyświetlana za mała, jeśli zostanie uruchomiona na komputerze, na którym czcionka systemowa jest w ciągu Tahoma 12 punktów. Elementy tekstowe, takie jak tytuły, menu, zawartość pola tekstowego itd., będą renderowane jako mniejsze niż inne aplikacje. Ponadto rozmiar elementów interfejsu użytkownika, które zawierają tekst, taki jak pasek tytułu, menu i wiele kontrolek, zależy od używanej czcionki. W tym przykładzie te elementy również będą widoczne stosunkowo małe.

Analogiczna sytuacja występuje, gdy aplikacja jest zaprojektowana pod kątem określonej rozdzielczości ekranu. Najczęściej spotykaną rozdzielczością jest 96 punktów na cal (DPI), co oznacza, że jest skalowanie ekranu o wartości 100%, ale wyższa rozdzielczość obejmuje 125%, 150%, 200% (odpowiednio równe 120, 144 i 192 DPI). Bez dostosowania aplikacja, szczególnie oparta na grafice, przeznaczona dla jednej rozdzielczości, będzie wyświetlana za duża lub za mała, gdy jest uruchamiana z inną rozdzielczością.

Automatyczne skalowanie pozwala ograniczyć te problemy przez automatyczne zmienianie rozmiaru formularza i jego formantów podrzędnych zgodnie z względnym rozmiarem czcionki lub rozdzielczością ekranu. System operacyjny Windows obsługuje automatyczne skalowanie okien dialogowych przy użyciu względnej jednostki miary zwanej jednostkami okna dialogowego. Jednostka okna dialogowego zależy od czcionki systemowej i jej relacji do pikseli można określić za pomocą funkcji Win32 SDK `GetDialogBaseUnits` . Gdy użytkownik zmieni motyw używany przez system Windows, wszystkie okna dialogowe są odpowiednio dostosowane. Ponadto .NET Framework obsługuje automatyczne skalowanie zgodnie z domyślną czcionką systemową lub rozdzielczością ekranu. Opcjonalnie Skalowanie automatyczne można wyłączyć w aplikacji.

## <a name="original-support-for-automatic-scaling"></a>Oryginalna obsługa automatycznego skalowania

Wersje 1,0 i 1,1 .NET Framework obsługują automatyczne skalowanie w prosty sposób, który jest zależny od domyślnej czcionki systemu Windows używanej przez interfejs użytkownika, reprezentowanej przez **DEFAULT_GUI_FONT**wartość zestawu Win32 SDK. Ta czcionka jest zazwyczaj zmieniana tylko w przypadku zmiany rozdzielczości ekranu. Do wdrożenia automatycznego skalowania użyto następującego mechanizmu:

1. W czasie projektowania <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> Właściwość (która jest obecnie przestarzała) została ustawiona na wysokość i szerokość domyślnej czcionki systemowej na komputerze dewelopera.

2. W czasie wykonywania domyślna czcionka systemowa komputera użytkownika została użyta do zainicjowania <xref:System.Windows.Forms.Control.Font%2A> właściwości <xref:System.Windows.Forms.Form> klasy.

3. Przed wyświetleniem formularza <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> Metoda została wywołana w celu skalowania formularza. Ta metoda oblicza względne rozmiary skalowania z <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> , a <xref:System.Windows.Forms.Control.Font%2A> następnie nazywa <xref:System.Windows.Forms.Control.Scale%2A> metodę, aby faktycznie skalować formularz i jego elementy podrzędne.

4. Wartość <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> została zaktualizowana tak, aby kolejne wywołania <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> nie zmieniały rozmiaru formularza.

Chociaż ten mechanizm wystarcza do większości celów, miało to wpływ na następujące ograniczenia:

- Ponieważ <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> Właściwość reprezentuje rozmiar czcionki linii bazowej jako wartości całkowite, występują błędy zaokrągleń, które stają się oczywiste, gdy formularz zostanie przetworzony przez wiele rozwiązań.

- Skalowanie automatyczne zostało zaimplementowane tylko w <xref:System.Windows.Forms.Form> klasie, a nie w <xref:System.Windows.Forms.ContainerControl> klasie. W związku z tym formanty użytkownika można skalować poprawnie tylko wtedy, gdy kontrolka użytkownika została zaprojektowana w taki sam sposób jak w formularzu i została umieszczona w formularzu w czasie projektowania.

- Formularze i ich kontrolki podrzędne mogą być współbieżnie zaprojektowane tylko przez wielu deweloperów, jeśli ich rozdzielczości są takie same. Podobnie również dziedziczenie formularza zależy od rozdzielczości skojarzonej z formularzem nadrzędnym.

- Nie jest on zgodny z nowszymi menedżerami układu wprowadzonymi w .NET Framework wersja 2,0, taka jak <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> .

- Nie obsługuje skalowania opartego bezpośrednio na rozdzielczości ekranu, która jest wymagana do .NET Compact Framework.

Mimo że ten mechanizm jest zachowywany w .NET Framework wersji 2,0 w celu zachowania zgodności z poprzednimi wersjami, został zastąpiony przez bardziej niezawodny mechanizm skalowania opisany dalej. W związku z tym,, <xref:System.Windows.Forms.Form.AutoScale%2A> , <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> i niektóre <xref:System.Windows.Forms.Control.Scale%2A> przeciążenia są oznaczone jako przestarzałe.

> [!NOTE]
> Po uaktualnieniu starszego kodu do .NET Framework w wersji 2,0 można bezpiecznie usunąć odwołania do tych członków.

## <a name="current-support-for-automatic-scaling"></a>Bieżąca obsługa automatycznego skalowania

.NET Framework w wersji 2,0 surmounts poprzednie ograniczenia, wprowadzając następujące zmiany w automatycznym skalowaniu Windows Forms:

- Podstawowa obsługa skalowania została przeniesiona do <xref:System.Windows.Forms.ContainerControl> klasy, tak aby formularze, natywne kontrolki złożone i kontrolki użytkownika otrzymywały obsługę jednolitego skalowania. Nowe elementy członkowskie <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> , <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> i <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> zostały dodane.

- <xref:System.Windows.Forms.Control>Klasa ma również kilka nowych członków, które umożliwiają działowi IT przeskalowanie i obsługę skalowania mieszanego na tym samym formularzu. W przypadku <xref:System.Windows.Forms.Control.Scale%2A> <xref:System.Windows.Forms.Control.ScaleChildren%2A> elementów członkowskich, i są <xref:System.Windows.Forms.Control.GetScaledBounds%2A> obsługiwane skalowanie.

- Dodano obsługę skalowania na podstawie rozdzielczości ekranu, aby uzupełnić obsługę czcionek systemowych, zgodnie z definicją w <xref:System.Windows.Forms.AutoScaleMode> wyliczeniu. Ten tryb jest zgodny z automatycznym skalowaniem obsługiwanym przez .NET Compact Framework umożliwiającym łatwiejsze Migrowanie aplikacji.

- Zgodność z menedżerami układu, takimi jak <xref:System.Windows.Forms.FlowLayoutPanel> i, została <xref:System.Windows.Forms.TableLayoutPanel> dodana do implementacji automatycznego skalowania.

- Czynniki skalowania są teraz reprezentowane jako wartości zmiennoprzecinkowe, zwykle przy użyciu <xref:System.Drawing.SizeF> struktury, dzięki czemu błędy zaokrągleń zostały praktycznie wyeliminowane.

> [!CAUTION]
> Nie są obsługiwane dowolne mieszanki trybów skalowania DPI i czcionek. Chociaż można skalować kontrolkę użytkownika przy użyciu jednego trybu (na przykład DPI) i umieścić ją w formularzu przy użyciu innego trybu (czcionki) bez problemów, ale mieszanie formularza podstawowego w jednym trybie, a formularz pochodny w innym może prowadzić do nieoczekiwanych wyników.

### <a name="automatic-scaling-in-action"></a>Automatyczne skalowanie w działaniu

Windows Forms teraz używa następującej logiki do automatycznego skalowania formularzy i ich zawartości:

1. W czasie projektowania każda z nich <xref:System.Windows.Forms.ContainerControl> rejestruje tryb skalowania i jego bieżącą rozdzielczość <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> odpowiednio w i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> .

2. W czasie wykonywania rzeczywiste rozwiązanie jest przechowywane we <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> właściwości. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>Właściwość dynamicznie oblicza stosunek między rozdzielczością skalowania w czasie wykonywania i w czasie projektowania.

3. Gdy formularz ładuje, jeśli wartości <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> są różne, <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> Metoda jest wywoływana w celu skalowania kontrolki i jej elementów podrzędnych. Ta metoda zawiesza układ i wywołuje metodę, <xref:System.Windows.Forms.Control.Scale%2A> Aby wykonać rzeczywiste skalowanie. Następnie wartość <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> jest aktualizowana, aby uniknąć stopniowego skalowania.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>jest również automatycznie wywoływany w następujących sytuacjach:

    - W odpowiedzi na <xref:System.Windows.Forms.Control.OnFontChanged%2A> zdarzenie, jeśli tryb skalowania to <xref:System.Windows.Forms.AutoScaleMode.Font> .

    - Gdy układ formantu kontenera zostanie wznowiony i zostanie wykryta zmiana we <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwościach lub.

    - Jak wspomniano powyżej, gdy element nadrzędny <xref:System.Windows.Forms.ContainerControl> jest skalowany. Każda kontrolka kontenera jest odpowiedzialna za skalowanie jej elementów podrzędnych przy użyciu własnych czynników skalowania, a nie z kontenera nadrzędnego.

5. Kontrolki podrzędne mogą modyfikować zachowanie skalowania za pomocą kilku metod:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A>Właściwość można zastąpić, aby określić, czy ich kontrolki podrzędne powinny być skalowane, czy nie.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A>Metoda może zostać przesłonięta w celu dostosowania granic, do których jest skalowana kontrolka, ale nie do logiki skalowania.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A>Metodę można zastąpić, aby zmienić logikę skalowania dla bieżącej kontrolki.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Renderowanie formantów przy użyciu stylów wizualnych](./controls/rendering-controls-with-visual-styles.md)
- [Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
