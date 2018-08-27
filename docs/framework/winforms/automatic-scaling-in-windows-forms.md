---
title: Automatyczne skalowanie w formularzach systemu Windows
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: d3981be7977b56af0b60f9796519b78dc9ac5db3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931654"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatyczne skalowanie w formularzach Windows Forms

Automatycznego skalowania umożliwia formularza i jego formantów, przeznaczone na jednym komputerze przy użyciu określonych wyświetlania systemu lub rozpoznawanie czcionki, mają być wyświetlane odpowiednio na innym komputerze przy użyciu czcionki systemu lub rozpoznawanie innego ekranu. Gwarantuje on, że formularz i jego formantów inteligentnie spowoduje zmianę rozmiaru, aby były zgodne z macierzystego systemu windows i innych aplikacji na komputerach z innymi deweloperami i użytkownika. Wsparcie [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] automatycznego skalowania i stylów wizualnych umożliwia [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji, aby utrzymać spójny wygląd i zachowanie w porównaniu do natywnych aplikacji Windows na komputerach poszczególnych użytkowników.

W większości przypadków, automatyczne skalowanie działa zgodnie z oczekiwaniami w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wersji 2.0 lub nowszej. Jednak zmiany schematu czcionek, może być problematyczne. Na przykład jak rozwiązać ten problem, zobacz [porady: odpowiadanie na zmiany schematu czcionek w aplikacji Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Potrzeby automatycznego skalowania

Bez skalowania automatycznego, aplikacja jest przeznaczona dla rozdzielczość ekranu co lub czcionki albo pojawi się zbyt małej lub zbyt duży podczas rozpoznawania lub czcionki zmodyfikowaniu. Na przykład jeśli aplikacja została zaprojektowana tak, przy użyciu punktu Tahoma 9 jako punkt odniesienia, bez dopasowania pojawi się zbyt mały uruchamiany na komputerze, gdzie czcionki systemowej jest punktem Tahoma 12. Elementy tekstu, takie jak tytuły, menu, zawartości pola tekstowego i tak dalej, że będzie mniejszy niż inne aplikacje. Ponadto rozmiar elementów interfejsu użytkownika, które zawierają tekst, takie jak pasek tytułu, menu i wielu formantów są zależne od czcionkę. W tym przykładzie te elementy zostaną również zostać wyświetlony stosunkowo mniejsze.

Taka sytuacja jest analogiczne występuje, gdy aplikacja jest przeznaczona dla niektórych rozdzielczość ekranu. Najbardziej typowe rozdzielczość ekranu jest 96 punktów na cal (DPI), która jest równa skalowanie ekranu 100%, ale wyświetlacze o wysokiej rozdzielczości obsługi 125%, 150%, 200% (które odpowiednio równy 120, 144 i 192 DPI) i nowszych stają się coraz bardziej powszechne. Bez dostosowania, aplikacji, szczególnie na podstawie grafiki jeden, przeznaczony dla jednego rozwiązania pojawi się zbyt duży lub za mały uruchamiania o inne rozwiązanie.

Automatyczne skalowanie ma na celu powodowane te problemy przez automatyczna zmiana rozmiaru w formularzu i jego formantów podrzędnych zgodnie z odpowiedniego rozmiaru czcionki lub rozdzielczość ekranu. System operacyjny Windows obsługuje automatyczne skalowanie przy użyciu względne jednostki miary o nazwie jednostki okna dialogowego w oknach dialogowych. Jednostki okna dialogowego opiera się na czcionki systemowej i jej relacji z pikseli, można jednak określić funkcję Win32 SDK `GetDialogBaseUnits`. Gdy użytkownik zmienia motyw użyty przez Windows, wszystkie okna dialogowe są automatycznie odpowiednio dostosowane. Ponadto [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] obsługuje automatyczne skalowanie, albo przy użyciu domyślnej czcionki systemowej, czy rozdzielczość ekranu. Opcjonalnie Skalowanie automatyczne można wyłączyć w aplikacji.

## <a name="original-support-for-automatic-scaling"></a>Oryginalny obsługę automatycznego skalowania

Wersje 1.0 i 1.1 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] obsługiwane automatyczne skalowanie w prosty sposób, który był zależny od Windows domyślną czcionkę dla interfejsu użytkownika, reprezentowany przez wartość Win32 SDK **DEFAULT_GUI_FONT**. Tę czcionkę zwykle jest zmieniany tylko w przypadku zmiany rozdzielczość ekranu. Następującego mechanizmu został użyty do wdrożenia, automatycznego skalowania:

1. W czasie projektowania <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (która jest już przestarzały) była właściwością wysokość i szerokość domyślnej czcionki systemowej na komputerze dewelopera.

2. W czasie wykonywania, domyślnej czcionki systemowej maszyny użytkownika został użyty do zainicjowania <xref:System.Windows.Forms.Control.Font%2A> właściwość <xref:System.Windows.Forms.Form> klasy.

3. Przed wyświetleniem formularza <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> wywołano metodę skalowania w formularzu. Ta metoda obliczane rozmiarach względnej skali od <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> i <xref:System.Windows.Forms.Control.Font%2A> następnie wywoływana <xref:System.Windows.Forms.Control.Scale%2A> metoda faktycznie skalowania w formularzu i jego elementów podrzędnych.

4. Wartość <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> został zaktualizowany tak oznacza kolejne wywołania <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> nie zmienił stopniowo rozmiaru formularza.

Podczas tego mechanizmu jest wystarczające w większości przypadków, jego jest z następującymi ograniczeniami:

- Ponieważ <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> właściwość reprezentuje rozmiar czcionki punktu odniesienia jako wartości całkowite, występują błędy zaokrągleń, które stają się oczywiste, po ponownym włączeniu formularza za pomocą wielu rozdzielczości.

- Automatyczne skalowanie został wdrożony tylko <xref:System.Windows.Forms.Form> klasy, nie w <xref:System.Windows.Forms.ContainerControl> klasy. W rezultacie kontrolki użytkownika będzie skalować poprawnie tylko wtedy, gdy formant użytkownika został zaprojektowany na tego samego rozwiązania co formularz i została umieszczona w postaci, w czasie projektowania.

- Formularzy i ich formantów podrzędnych może być jednocześnie przeznaczona wyłącznie przez wielu deweloperów dostępnych rozwiązaniach poszczególnych problemów maszyny były takie same. Podobnie on również dziedziczenia formularza zależy od rozdzielczości skojarzone z formularza nadrzędnego.

- Nie jest zgodny z nowszą menedżerów układu wprowadzone w programie [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0, takich jak <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.

- Nie obsługuje skalowania oparty bezpośrednio na rozdzielczość ekranu, który jest wymagane dla zachowania zgodności, aby [!INCLUDE[compact](../../../includes/compact-md.md)].

Mimo że ten mechanizm jest zachowywana w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0 w celu zachowania zgodności z poprzednimi wersjami, została zastąpiona przez bardziej niezawodny mechanizm skalowania opisane w dalszej części. W konsekwencji <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>, a niektóre <xref:System.Windows.Forms.Control.Scale%2A> przeciążenia są oznaczone jako przestarzałe.

> [!NOTE]
> Można bezpiecznie usunąć odwołania do tych członków, podczas uaktualniania starszego kodu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0.

## <a name="current-support-for-automatic-scaling"></a>Bieżący obsługę automatycznego skalowania

[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0 surmounts wcześniejszych ograniczeń, wprowadzając następujące zmiany do automatycznego skalowania dla formularzy Windows:

- Podstawowa pomoc techniczna dla skalowania została przeniesiona do <xref:System.Windows.Forms.ContainerControl> klasy tak, aby formularze, kontrolki złożonej natywne i formanty użytkownika wszystkie uzyskania jednolitego skalowania pomocy technicznej. Nowi członkowie <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> i <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> zostały dodane.

- <xref:System.Windows.Forms.Control> Klasa ma również kilka nowych członków, zezwalające do wzięcia udziału w skalowania i obsługi mieszane skalowanie na tym samym formularzu. W szczególności <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, i <xref:System.Windows.Forms.Control.GetScaledBounds%2A> wspierać członków.

- W przypadku skalowania na podstawie rozdzielczości ekranu dodano obsługę jako uzupełnienie obsługi czcionki systemowej, zgodnie z definicją <xref:System.Windows.Forms.AutoScaleMode> wyliczenia. Ten tryb jest zgodny z automatycznego skalowania, obsługiwane przez [!INCLUDE[compact](../../../includes/compact-md.md)] Włączanie łatwiejsza migracja aplikacji.

- Zgodność z menedżerów układu, takie jak <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> została dodana do wykonania automatycznego skalowania.

- Czynniki skalowania są teraz reprezentowane jako wartości, zazwyczaj przy użyciu zmiennoprzecinkowych <xref:System.Drawing.SizeF> struktury, tak aby błędy zaokrągleń zostały wyeliminowane praktycznie.

> [!CAUTION]
> Dowolne mieszanki DPI i skalowania tryby czcionki nie są obsługiwane. Mimo że może skalować kontrolki użytkownika przy użyciu trybu (na przykład DPI) i umieść go w formularzu za pomocą innego trybu (czcionka) bez żadnych problemów, ale mieszanie formularza podstawowego w trybie jednego i pochodnej formularza w innym może prowadzić do nieoczekiwanych wyników.

### <a name="automatic-scaling-in-action"></a>Automatyczne skalowanie w akcji

Formularze Windows używa teraz Poniższa logika automatycznego skalowania, formularzy i ich zawartość:

1. W czasie projektowania każdy <xref:System.Windows.Forms.ContainerControl> rejestruje trybu skalowania i aktualna rozdzielczość w <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, odpowiednio.

2. W czasie wykonywania, rzeczywistej rozdzielczości są przechowywane w <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> właściwości. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Właściwość dynamicznie obliczy stosunek rozpoznawania skalowania środowiska wykonawczego i w czasie projektowania.

3. Podczas ładowania formularza, jeśli wartości <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> są różne, a następnie <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> metoda jest wywoływana w celu skalowania formantem i jego elementów podrzędnych. Ta metoda wstrzymuje układ i wywołania <xref:System.Windows.Forms.Control.Scale%2A> metodę w celu rzeczywiste skalowanie. Później, wartość <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> zostanie zaktualizowany w celu uniknięcia stopniowego skalowania.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> automatycznie jest wywoływana w następujących sytuacjach:

    - W odpowiedzi na <xref:System.Windows.Forms.Control.OnFontChanged%2A> zdarzeń, jeśli jest to tryb skalowania <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Po wykryciu układu wznawia kontroli kontenera i zmiany w <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> lub <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości.

    - Jako niejawnego powyżej, gdy element nadrzędny <xref:System.Windows.Forms.ContainerControl> wykonywane jest skalowanie. Każdy formant kontenera jest odpowiedzialny za skalowanie jego elementy podrzędne przy użyciu własnej skalowanie czynników, a nie jednego z jej kontenera nadrzędnego.

5. Formanty podrzędne można zmodyfikować, aby ich zachowanie skalowania za pomocą kilku środków:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Właściwość może być zastąpiona w celu ustalenia, jeśli jego formantów podrzędnych powinny być skalowane.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Metodę można przesłonić, aby dopasować granice, które kontrolki są skalowane do, ale nie skalowanie logika.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Metodę można przesłonić, aby zmienić skalowanie logika kontrolą bieżącą.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Renderowanie kontrolek przy użyciu stylów wizualnych](./controls/rendering-controls-with-visual-styles.md)
- [Instrukcje: poprawianie wydajności dzięki unikaniu automatycznego skalowania](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)