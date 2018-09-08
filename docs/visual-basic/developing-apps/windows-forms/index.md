---
title: Podstawy dotyczące aplikacji Windows Forms (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: b900b85b4e3e56dbc587a15edea40f6e3032cbd1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192434"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Podstawy dotyczące aplikacji Windows Forms (Visual Basic)
Ważną częścią programu Visual Basic jest możliwość tworzenia aplikacji Windows Forms, które działają lokalnie na komputerach użytkowników. Visual Studio umożliwia tworzenie aplikacji i interfejsu użytkownika przy użyciu Windows Forms. Aplikacja Windows Forms jest oparta na klasy z <xref:System.Windows.Forms> przestrzeni nazw.  
  
## <a name="designing-windows-forms-applications"></a>Aplikacje projektowania Windows Forms  
 Windows Forms i aplikacji usług Windows można utworzyć za pomocą programu Visual Studio. Więcej informacji znajduje się w następujących tematach:  
  
-   [Wprowadzenie do formularzy Windows](../../../framework/winforms/getting-started-with-windows-forms.md). Zawiera informacje dotyczące sposobu tworzenia i programu Windows Forms.  
   
-   [Kontrolki formularzy Windows Forms](../../../framework/winforms/controls/index.md). Kolekcja tematów szczegółowych informacji na temat użytkowania kontrolek formularzy Windows Forms.  
  
-   [Windows, usługi aplikacji](../../../framework/windows-services/index.md). Wyświetla listę tematów, które opisują sposób tworzenia usług Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Interfejsy użytkownika bogate, interaktywne tworzenie  
 Formularze Windows to składnik klienta inteligentnych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], zbiór bibliotek zarządzanych, które umożliwiają typowych zadań aplikacji, takich jak odczytywanie i zapisywanie w systemie plików. Używanie środowiska programistycznego, takimi jak Visual Studio, możesz tworzyć aplikacje Windows Forms, do wyświetlania informacji, żądać danych wejściowych od użytkowników i komunikować się ze zdalnymi komputerami za pośrednictwem sieci.  
  
 W formularzach Windows Forms formularz jest powierzchnią wizualną, na którym możesz wyświetlić informacje do użytkownika. Często możesz tworzyć aplikacje Windows Forms, umieszczając formantów na formularzach i tworzenia odpowiedzi na działania użytkownika, takich jak kliknięcia lub naciśnięcia klawiszy. A *kontroli* jest element interfejsu użytkownika dyskretnych, który wyświetla dane lub akceptuje dane wejściowe.  
  
### <a name="events"></a>Zdarzenia  
 Gdy użytkownik wykona coś do formularza lub jego formantów, generuje zdarzenie. Aplikacja reaguje na zdarzenia przy użyciu kodu i przetwarza zdarzenia w momencie ich wystąpienia. Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Formanty  
 Windows Forms zawiera szereg formantów, które można umieścić w formularzach: formantów, które wyświetlają pola tekstowe, przyciski, pola listy rozwijanej, przyciski radiowe i nawet stron sieci Web. Aby uzyskać listę wszystkich kontrolek, można użyć w formularzu, zobacz [kontrolki do użycia w formularzach Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli formant nie spełnia Twoich potrzeb, formularze Windows obsługuje również tworzenie własnych niestandardowych kontrolek przy użyciu <xref:System.Windows.Forms.UserControl> klasy.  
  
 Formularze Windows ma zaawansowanych kontrolek interfejsu użytkownika, które emulują funkcji wysokiej jakości aplikacji, takie jak Microsoft Office. Za pomocą <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip> kontrolki, możesz utworzyć pasków narzędzi i menu, które zawierają tekst i obrazy, wyświetlić podmenu i hostują inne kontrolki, takie jak pola tekstowe i pola kombi.  
  
 Za pomocą projektanta formularzy przeciągnij i upuść programu Visual Studio, możesz łatwo tworzyć aplikacje Windows Forms: po prostu wybierz kontrolki, należy umieścić kursor i umieść je w miejscu w formularzu. Projektant udostępnia narzędzia, takie jak linii siatki i "linii przyciągania" Aby uprości wyrównywanie formantów. Czy przy użyciu programu Visual Studio lub kompilacji w wierszu polecenia, można użyć <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.SplitContainer> służy do tworzenia zaawansowanych tworzą układy przy użyciu minimalnego czasu i wysiłku.  
  
### <a name="custom-ui-elements"></a>Elementy interfejsu użytkownika  
 Na koniec, jeśli musisz utworzyć własne niestandardowe elementy interfejsu użytkownika <xref:System.Drawing> przestrzeń nazw zawiera wszystkie klasy, należy renderować linii, okręgi i inne kształty bezpośrednio na formularzu.  
  
 Aby uzyskać szczegółowe informacje na temat korzystania z tych funkcji zobacz następujące tematy Pomocy.  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Tworzenie nowej aplikacji Windows Forms przy użyciu programu Visual Studio|[Wskazówki: Tworzenie formularza Windows prosty](https://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Użyj kontrolek na formularzach|[Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Tworzenia grafiki przy użyciu <xref:System.Drawing>|[Wprowadzenie do programowania grafiki](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Tworzenie niestandardowych formantów|[Instrukcje: dziedziczenie z klasy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Wyświetlanie i manipulowanie danymi  
 Wiele aplikacji, musisz wyświetlić dane z bazy danych, plik XML, usługi XML sieci Web lub innego źródła danych. Formularze Windows udostępnia elastyczną kontrolę, wywoływana <xref:System.Windows.Forms.DataGridView> kontroli renderowania takich danych tabelarycznych w tradycyjnych formacie wierszy i kolumn, tak aby każdy element danych zajmował komórki. Za pomocą <xref:System.Windows.Forms.DataGridView> można dostosować wygląd pojedyncze komórki, dowolnego wierszy i kolumn w miejscu i wyświetlić złożonych kontrolek w komórkach, m.in.  
  
 Łączenie ze źródłami danych za pośrednictwem sieci jest prostym zadaniem przy użyciu klienci inteligentni Windows Forms. <xref:System.Windows.Forms.BindingSource> Składnika, nowe za pomocą usługi Windows Forms w [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] i [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)]reprezentuje połączenie ze źródłem danych i udostępnia metody powiązanie danych z kontrolkami, przejdź do poprzedniego i dalej rekordów, edytowanie rekordów i zapisywanie zmiany z powrotem do oryginalnego źródła. <xref:System.Windows.Forms.BindingNavigator> Kontroli udostępnia prosty interfejs, za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnika umożliwiające użytkownikom przechodzenie między rekordami.  
  
### <a name="data-bound-controls"></a>Formanty powiązane z danymi  
 Możesz utworzyć formanty powiązane z danymi za pomocą okna źródeł danych, który wyświetla źródła danych, takich jak bazy danych, usług sieci Web i obiekty w projekcie. Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z tego okna na formularze w projekcie. Użytkownik może również wiązania danych istniejących kontrolek z danymi przez przeciąganie obiektów z okna źródeł danych na istniejące kontrolki.  
  
### <a name="settings"></a>Ustawienia  
 Inny typ wiązania danych, którymi można zarządzać w formularzach Windows Forms jest ustawień. Większość inteligentnych aplikacji klienckich należy zachować pewne informacje o ich stanie w czasie wykonywania, takie jak rozmiar Ostatnia znana formularzy i Zachowaj dane preferencje użytkownika, takie jak domyślne lokalizacje zapisane pliki. Ustawienia aplikacji funkcji rozwiązuje te wymagania, zapewniając łatwy sposób przechowywania oba rodzaje ustawień na komputerze klienckim. Po zdefiniowaniu, za pomocą programu Visual Studio lub Edytor kodu, te ustawienia są utrwalane w formacie XML i automatycznie odczytywać powrotem do pamięci w czasie wykonywania.  
  
 Aby uzyskać szczegółowe informacje na temat korzystania z tych funkcji zobacz następujące tematy Pomocy.  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Użyj <xref:System.Windows.Forms.BindingSource> składnika|[Instrukcje: powiązywanie kontrolek formularzy Windows Forms ze składnikiem BindingSource przy użyciu narzędzia Projektant](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Praca z [!INCLUDE[vstecado](~/includes/vstecado-md.md)] źródeł danych|[Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Korzystanie z okna źródeł danych|[Wskazówki: Wyświetlanie danych w formularzu Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Wdrażanie aplikacji na komputerach klienckich  
 Napisana aplikacja trzeba wysłać ją do użytkowników, tak, aby zainstalować i uruchomić ją na komputerach klienckich. Za pomocą [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] technologii, można wdrażać aplikacje z poziomu programu Visual Studio za pomocą kilku kliknięć i udostępniać użytkownikom adres URL wskazujący aplikację w sieci Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] zarządza wszystkie elementy i zależności w aplikacji oraz zapewnia, że aplikacja jest poprawnie zainstalowana na komputerze klienckim.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacje mogą być skonfigurowane do uruchamiania tylko wtedy, gdy użytkownik jest połączony z siecią lub uruchomić zarówno w trybie online i offline. Po określeniu, czy aplikacja powinna obsługiwać operacji w trybie offline, [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] dodaje łącze do aplikacji użytkownika **Start** menu, dzięki czemu użytkownik może go otwierać bez korzystania z adresu URL.  
  
 Podczas aktualizacji aplikacji, możesz opublikować nowy manifest wdrożenia i nową kopię aplikacji na serwerze sieci Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] wykrywa, że nie jest dostępna aktualizacja i uaktualnień instalacji przez użytkownika; nie niestandardowych programów jest wymagany do zaktualizowania starej zestawów.  
  
 Aby uzyskać pełne wprowadzenie do [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowe informacje na temat korzystania z tych funkcji zobacz poniższe tematy pomocy:  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Wdrażanie aplikacji za pomocą [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizacja [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] wdrożenia|[Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Zarządzanie zabezpieczeniami za pomocą [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Inne formanty i funkcje  
 Istnieje wiele innych funkcji w formularzach Windows Forms, wchodzące Implementowanie typowych zadań, szybkie i łatwe, takie jak obsługa tworzenie okien dialogowych, drukowanie, dodając pomocy i dokumentacji i lokalizowanie aplikacji na wiele języków. Ponadto, formularze Windows opiera się na niezawodne zabezpieczenia systemu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], dzięki czemu można zwolnić bardziej bezpieczne aplikacje swoim klientom.  
  
 Aby uzyskać szczegółowe informacje na temat korzystania z tych funkcji zobacz poniższe tematy pomocy:  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Drukowanie zawartości formularza|[Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Więcej informacji na temat zabezpieczeń Windows Forms|[Przegląd zabezpieczeń w formularzach Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
- [Windows Forms — omówienie](../../../framework/winforms/windows-forms-overview.md)  
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
