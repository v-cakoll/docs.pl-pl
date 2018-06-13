---
title: Automatyczne skalowanie w formularzach systemu Windows
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: e27c56d9a6d745c7d1ff83986e7996aa1bebc879
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529886"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatyczne skalowanie w formularzach systemu Windows
Umożliwia skalowanie automatyczne formularza i jego formantów pozwala na jednej maszynie czcionką niektórych wyświetlania rozwiązania lub system, wyświetlane odpowiednio na inny komputer o czcionki różne rozwiązania lub systemu. Gwarantuje on, że formularz i jego formantów inteligentnie spowoduje zmianę rozmiaru, aby były spójne z macierzystego systemu windows i innych aplikacji na komputerach z innymi deweloperami i użytkownika. Obsługę [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] automatyczne skalowanie i style wizualne umożliwia [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacje do obsługi spójny wygląd i zachowanie w porównaniu do natywnych aplikacji systemu Windows na komputerze każdego użytkownika.
  
W większości przypadków automatyczne skalowanie działa zgodnie z oczekiwaniami w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0 lub nowszej. Jednak zmiany schematu czcionek może sprawiać problemy. Aby zapoznać się przykładem rozwiązać ten problem, zobacz [porady: odpowiadanie na zmiany schematu czcionek w aplikacji formularzy systemu Windows](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).
  
## <a name="need-for-automatic-scaling"></a>Potrzebę automatyczne skalowanie  
Bez automatycznego skalowania aplikacji przeznaczony dla jednego rozdzielczości lub czcionki albo pojawi się zbyt małej lub zbyt duży podczas rozpoznawania lub czcionki zostanie zmieniona. Na przykład jeśli aplikacja została opracowana za pomocą punktu Tahoma 9 jako linii bazowej, bez dopasowania pojawi się zbyt mały Uruchom na komputerze, którym czcionki systemowej Tahoma 12 punktu. Tekst elementów, takich jak tytuły, menu zawartości pola tekstowego i tak dalej spowoduje, że mniejszy niż inne aplikacje. Ponadto rozmiar elementów interfejsu użytkownika, które zawierają tekstu, na przykład na pasku tytułu, menu i wielu formantów są zależne od używanej czcionki. W tym przykładzie te elementy są również pojawi się stosunkowo mniejsze.

Analogiczna sytuacja występuje, gdy aplikacja jest przeznaczona dla niektórych rozdzielczość ekranu. Najbardziej typowe rozdzielczość ekranu jest 96 punktów na cal (DPI), który wynosi 100% skalowanie ekranu, ale wyświetlacze o wysokiej rozdzielczości obsługi 125%, 150%, 200% (które odpowiednio równy 120, 144 i 192 DPI) i nowszych stają się coraz bardziej powszechne. Bez dopasowania, aplikacji, szczególnie grafiki na podstawie jednej, przeznaczony dla jednego rozdzielczości będą wyświetlane jest za duża albo za mała uruchomienia na inne rozwiązanie.

Automatyczne skalowanie ma na celu rzecz poprawy funkcjonowania te problemy przez automatyczna zmiana rozmiaru formularza i jej kontrolkach podrzędnych zgodnie z odpowiedniego rozmiaru czcionki lub rozdzielczości ekranu. System operacyjny Windows obsługuje automatyczne skalowanie okien dialogowych za pomocą względną jednostki miary o nazwie jednostki okna dialogowego. Jednostki okna dialogowego jest oparta na czcionki systemowej i ich relacji z pikseli może być jednak określić funkcji Win32 SDK `GetDialogBaseUnits`. Gdy użytkownik zmienia motywu używanego przez system Windows, wszystkie okna dialogowe są automatycznie dostosowana. Ponadto [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] obsługuje automatyczne skalowanie, albo zgodnie z domyślnej czcionki systemowej lub rozdzielczość ekranu. Opcjonalnie automatyczne skalowanie można wyłączyć w aplikacji.

## <a name="original-support-for-automatic-scaling"></a>Oryginalny obsługę automatyczne skalowanie
W wersjach 1.0 i 1.1 z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] obsługiwane automatyczne skalowanie w sposób prostego zależał Windows domyślną czcionkę interfejsu użytkownika, reprezentowany przez wartość Win32 SDK **DEFAULT_GUI_FONT**. Tę czcionkę zwykle jest zmieniane tylko gdy zmienia się rozdzielczość ekranu. Następującego mechanizmu został użyty do wdrożenia skalowania automatycznego:

1. W czasie projektowania <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> ustawiono właściwość (która jest teraz przestarzałe) wysokość i szerokość domyślnej czcionki systemowej na komputerze dewelopera.

2. W czasie wykonywania, domyślnej czcionki systemowej maszyny użytkownika został użyty do zainicjowania <xref:System.Windows.Forms.Control.Font%2A> właściwość <xref:System.Windows.Forms.Form> klasy.

3. Przed wyświetleniem formularzu <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> wywołano metodę skalowania formularza. Ta metoda obliczana rozmiary skali względnej z <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> i <xref:System.Windows.Forms.Control.Font%2A> następnie wywołuje <xref:System.Windows.Forms.Control.Scale%2A> metody faktycznie skalowania formularz i jego elementów podrzędnych.

4. Wartość <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> został zaktualizowany tak to kolejnych wywołań <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> nie zmienił stopniowo rozmiaru formularza.

Podczas wystarczające w większości przypadków ten mechanizm odniesionej go z następującymi ograniczeniami:

- Ponieważ <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> właściwość reprezentuje rozmiar czcionki linii bazowej jako wartości całkowite, wystąpią błędy zaokrąglania, które stają się oczywiste po ponownym włączeniu formularza za pomocą wielu rozwiązania.

- Automatyczne skalowanie został wdrożony tylko <xref:System.Windows.Forms.Form> klasy nie w <xref:System.Windows.Forms.ContainerControl> klasy. W związku z tym kontrolek użytkownika będzie skalować poprawnie tylko wtedy, gdy formant użytkownika został zaprojektowany na taką samą rozdzielczość formularza i została umieszczona w postaci, w czasie projektowania.

- Formularzy i ich formantów podrzędnych może być jednocześnie przeznaczona wyłącznie przez deweloperów w wielu jeśli ich rozwiązania maszyny są takie same. Podobnie on również dziedziczenia formularza zależne od rozdzielczości skojarzone z formularza nadrzędnego.

> [!NOTE]
> Z najwyższą różnice w wyświetlania DPIs, szczególnie w nowoczesnych urządzeń 2-in-1 nadal możliwe z najnowszej wersji programu .NET Framework i Visual Studio. Aby rozwiązać ten w zespół przy użyciu różnych Wyświetla wartość DPI, zawsze upewnij się, że program Visual Studio, Projektant formularzy systemu Windows zawsze podstawowych obliczeń układu 96 DPI uruchamia w trybie bez-obsługującą ustawienia DPI. W tym celu wystarczy ustawić następujący klucz rejestru, aby wyłączyć świadomości HighDPI programu Visual Studio:
>
> ```
> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe]
> "dpiAwareness"=dword:00000000
> ```

- Nie jest zgodny z nowszą menedżerów układu wprowadzone w systemie [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0, takie jak <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.

- Nie obsługuje skalowania oparty bezpośrednio na rozdzielczość ekranu, wymaganego do zgodność z [!INCLUDE[compact](../../../includes/compact-md.md)].

Chociaż ten mechanizm jest zachowywana w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0 w celu zachowania zgodności z poprzednimi wersjami, została zastąpiona przez bardziej niezawodne skalowania mechanizm opisane w dalszej części. W konsekwencji <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>, a niektóre <xref:System.Windows.Forms.Control.Scale%2A> przeciążenia są oznaczone jako przestarzałe.

> [!NOTE]
> Można bezpiecznie usunąć odwołania do tych elementów członkowskich, podczas uaktualniania starszego kodu do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0.

## <a name="current-support-for-automatic-scaling"></a>Bieżąca obsługa automatyczne skalowanie
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 2.0 surmounts poprzedniego ograniczenia, wprowadzając następujące zmiany do skalowania automatycznego formularzy systemu Windows:

- Podstawowy obsługę skalowanie został przeniesiony do <xref:System.Windows.Forms.ContainerControl> klasy, aby otrzymały formularze, kontrolki natywne złożonego i kontrolek użytkownika wszystkie uniform skalowania pomocy technicznej. Nowe elementy członkowskie <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> i <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> zostały dodane.

- <xref:System.Windows.Forms.Control> Klasa ma również kilka nowych elementów członkowskich, które umożliwić mu uczestniczenie w skalowanie i do obsługi mieszanym skalowanie na tym samym formularzu. W szczególności <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, i <xref:System.Windows.Forms.Control.GetScaledBounds%2A> skalowania elementów członkowskich.

- Do skalowania ustalane na podstawie rozdzielczości ekranu dodano obsługę uzupełnienie obsługi czcionki systemowej, zgodnie z definicją <xref:System.Windows.Forms.AutoScaleMode> wyliczenia. Ten tryb jest zgodny z obsługiwanych przez skalowanie automatyczne [!INCLUDE[compact](../../../includes/compact-md.md)] włączenie łatwiejsze migracji aplikacji.

- Zgodność z menedżerów układu, takich jak <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel> został dodany do wdrożenia Skalowanie automatyczne.

- Czynniki skalowania teraz są reprezentowane jako przestawne wartości, zwykle za pomocą <xref:System.Drawing.SizeF> struktury, dzięki czemu praktycznie wyeliminowaniu błędów zaokrąglania.

> [!CAUTION]
> Dowolne mieszanki DPI i skalowania tryby czcionki nie są obsługiwane. Mimo że może skalowania formantu użytkownika przy użyciu trybu (na przykład DPI) i umieść go w formie przy użyciu innego trybu (czcionki) bez problemów, ale mieszanie formularza podstawowego w trybie jednego i pochodne formularza w innym może prowadzić do nieoczekiwanych wyników.

### <a name="automatic-scaling-in-action"></a>Automatyczne skalowanie w akcji
Formularze systemu Windows używa teraz następującą logiką automatycznie skalować formularzy i ich zawartość:

1. W czasie projektowania każdy <xref:System.Windows.Forms.ContainerControl> rejestruje bieżącego rozwiązania w trybie skalowanie i <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>odpowiednio.

2. W czasie wykonywania, rzeczywiste rozwiązania są przechowywane w <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> właściwości. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Właściwości dynamicznie oblicza stosunek rozpoznawania skalowania środowiska wykonawczego i czasu projektowania.

3. Podczas ładowania formularza, jeśli wartości <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> i <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> są różne, a następnie <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> wywoływana jest metoda skalowania formantu i jego elementów podrzędnych. Ta metoda wstrzymuje układ i wywołania <xref:System.Windows.Forms.Control.Scale%2A> metodę w celu skalowania rzeczywistych. Później, wartość <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> jest aktualizowana w celu uniknięcia stopniowego skalowania.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> jest również wywoływana automatycznie, w następujących sytuacjach:

    - W odpowiedzi na <xref:System.Windows.Forms.Control.OnFontChanged%2A> zdarzeń, jeśli tryb skalowania jest <xref:System.Windows.Forms.AutoScaleMode.Font>.
  
    - Po wykryciu układu wznawia formantu kontenera i zmiany w <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> lub <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości.
  
    - Jako niejawnego powyżej, gdy element nadrzędny <xref:System.Windows.Forms.ContainerControl> wykonywane jest skalowanie. Każdy kontener jest odpowiedzialny za skalowanie podrzędnych za pomocą własnego skalowanie czynniki i nie jeden z jego kontenera nadrzędnego.

5. Formanty podrzędne można zmodyfikować ich zachowanie skalowania za pomocą kilku środków:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Właściwości może zostać zastąpiona w celu określenia, czy ich formantów podrzędnych powinien być skalowany.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Metodę można przesłonić, aby dopasować granice, które formant są skalowane w celu, ale nie logiki skalowania.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Metodę można przesłonić, aby zmienić skalowania logikę bieżącego formantu.

## <a name="see-also"></a>Zobacz także
 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>  
 <xref:System.Windows.Forms.Control.Scale%2A>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](./controls/rendering-controls-with-visual-styles.md)  
 [Instrukcje: poprawianie wydajności dzięki unikaniu automatycznego skalowania](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
