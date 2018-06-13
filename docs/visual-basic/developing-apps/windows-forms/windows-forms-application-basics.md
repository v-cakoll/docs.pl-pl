---
title: Podstawy dotyczące aplikacji Windows Forms (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 051c2be00ca18799eeb2f5253a9b236bbcf82d21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592382"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Podstawy dotyczące aplikacji Windows Forms (Visual Basic)
Ważnym elementem języka Visual Basic jest możliwość tworzenia aplikacji formularzy systemu Windows, które są uruchamiane lokalnie na komputerach użytkowników. Visual Studio służy do tworzenia aplikacji i interfejs, za pomocą formularzy systemu Windows. Aplikacji formularzy systemu Windows jest oparty na klas z <xref:System.Windows.Forms> przestrzeni nazw.  
  
## <a name="designing-windows-forms-applications"></a>Aplikacje projektowania Windows Forms  
 Możesz utworzyć formularzy systemu Windows i aplikacji usług systemu Windows z programem Visual Studio. Więcej informacji znajduje się w następujących tematach:  
  
-   [Wprowadzenie do formularzy systemu Windows](../../../framework/winforms/getting-started-with-windows-forms.md). Zawiera informacje dotyczące sposobu tworzenia i program Windows Forms.  
   
-   [Formanty formularzy systemu Windows](../../../framework/winforms/controls/index.md). Kolekcja tematów wyszczególnieniem korzystanie z formantów formularzy systemu Windows.  
  
-   [Aplikacje usług systemu Windows](../../../framework/windows-services/index.md). Wyświetla listę tematów, które zawierają opis tworzenia usług systemu Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Tworzenie interfejsów użytkownika rozbudowanych, interakcyjnych  
 Formularze systemu Windows to składnik klienta inteligentnych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], zestaw zarządzanych bibliotek, które umożliwiają typowych zadań aplikacji, takich jak odczytywanie i zapisywanie do systemu plików. W środowisku programowania, takimi jak Visual Studio, można utworzyć aplikacji formularzy systemu Windows, które zawierają informacje, żądać danych wejściowych od użytkowników i komunikować się ze zdalnymi komputerami za pośrednictwem sieci.  
  
 W formularzach systemu Windows formularz jest visual powierzchni, na którym można wyświetlić informacje dla użytkownika. Często w przypadku tworzenia aplikacji formularzy systemu Windows, umieszczając formantów na formularzach i tworzenie odpowiedzi na działania użytkownika, takie jak kliknięcie myszą lub naciśnięcie klawiszy. A *kontroli* jest elementem interfejsu odrębny użytkownika, który wyświetla dane lub akceptuje dane wejściowe.  
  
### <a name="events"></a>Zdarzenia  
 Gdy użytkownik wykona coś do formularza lub jednego z jego formantów, generuje zdarzenie. Aplikacja reaguje na zdarzenia te przy użyciu kodu i przetwarza zdarzenia wystąpieniach. Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Formanty  
 Formularze systemu Windows zawiera różne formantów, które można umieścić w formularzach: formanty zawierające pola tekstowe, przycisków rozwijanych, przyciski radiowe i nawet stron sieci Web. Aby uzyskać listę wszystkich kontrolek, można użyć w formularzu, zobacz [formanty do użycia w formularzach systemu Windows](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli formant nie spełnia Twoje potrzeby, formularze systemu Windows obsługuje także tworzenie własnych niestandardowych formantów przy użyciu <xref:System.Windows.Forms.UserControl> klasy.  
  
 Formularze systemu Windows ma sformatowanego kontrolek interfejsu użytkownika, które emulują funkcje wysokiej jakości aplikacji, takich jak Microsoft Office. Przy użyciu <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip> formantu, można utworzyć paski narzędzi i menu, które zawierają tekst i obrazy, wyświetlania podmenu i udostępniać inne formanty, takie jak pola tekstowe i pola kombi.  
  
 Za pomocą programu Visual Studio projektanta formularzy przeciągania i upuszczania, można łatwo utworzyć aplikacji formularzy systemu Windows: po prostu zaznacz formantów kursor i umieść je w miejscu w formularzu. Projektant udostępnia narzędzia, takie jak linie siatki i "linie przyciągania" podjęcie proste poza wyrównywanie formantów. Czy za pomocą programu Visual Studio lub kompilacji w wierszu polecenia, można użyć <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.SplitContainer> służy do tworzenia zaawansowanych tworzą układów z minimalnym czasem i pracą.  
  
### <a name="custom-ui-elements"></a>Elementy interfejsu użytkownika  
 Na koniec, jeśli musisz utworzyć własne niestandardowe elementy interfejsu użytkownika <xref:System.Drawing> przestrzeń nazw zawiera wszystkie klasy, należy renderować linii, okręgi i innych kształtów bezpośrednio na formularzu.  
  
 Aby uzyskać szczegółowe informacje dotyczące korzystania z tych funkcji zobacz poniższe tematy Pomocy.  
  
|Do|Zobacz|  
|--------|---------|  
|Tworzenie nowej aplikacji formularzy systemu Windows z programem Visual Studio|[Wskazówki: Tworzenie formularza prostego systemu Windows](http://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Używanie formantów na formularzach|[Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Tworzenie grafiki <xref:System.Drawing>|[Wprowadzenie do programowania grafiki](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Tworzenie niestandardowych formantów|[Instrukcje: dziedziczenie z klasy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Wyświetlanie danych i operowanie nimi  
 Wiele aplikacji musi zawierać dane z bazy danych, plik XML, usługi XML sieci Web lub innego źródła danych. Formularze systemu Windows udostępnia elastyczną kontrolę o nazwie <xref:System.Windows.Forms.DataGridView> formantu do renderowania takich danych tabelarycznych w tradycyjnych formacie wierszy i kolumn, tak aby każdy element danych zajmuje komórki. Przy użyciu <xref:System.Windows.Forms.DataGridView> można dostosować wygląd pojedynczych komórek, dowolnego wierszy i kolumn w miejscu i wyświetlić złożonych kontrolek wewnątrz komórek, między innymi funkcjami.  
  
 Łączenie ze źródłami danych w sieci jest prostym zadaniem z klientami inteligentne formularzy systemu Windows. <xref:System.Windows.Forms.BindingSource> Składnika nowych z formularzy systemu Windows w [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] i [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)]reprezentuje połączenie ze źródłem danych i opisuje metody powiązanie danych z formantami, przechodząc do poprzedniego i następnego rekordów, edytowanie rekordów i zapisywanie zmian z powrotem do oryginalnego źródła. <xref:System.Windows.Forms.BindingNavigator> Kontroli udostępnia prosty interfejs w porównaniu z <xref:System.Windows.Forms.BindingSource> składnika użytkownikom przechodzenie między rekordów.  
  
### <a name="data-bound-controls"></a>Formanty powiązane z danymi  
 Można utworzyć za pomocą okna źródeł danych, który zawiera źródeł danych, takich jak bazy danych, usługi sieci Web i obiektów w projekcie formantów powiązanych z danymi. Formanty powiązane z danymi można utworzyć, przeciągając elementy z tego okna na formularze w projekcie. Użytkownik może również wiązania danych istniejących formantów do danych przeciągając obiekty z okna źródeł danych na istniejące kontrolki.  
  
### <a name="settings"></a>Ustawienia  
 Innego typu powiązania danych, którymi można zarządzać w formularzach systemu Windows jest ustawienia. Większość aplikacji inteligentnych klientów należy zachować niektóre informacje na temat ich stanu czasu wykonywania, takich jak rozmiar Ostatnia znana formularzy i zachowania danych użytkownika — preferencji, takich jak domyślne lokalizacje zapisane pliki. Funkcja ustawienia aplikacji adresy te wymagania, zapewniając łatwy sposób przechowywania obu typów ustawień na komputerze klienckim. Po zdefiniowaniu przy użyciu programu Visual Studio lub edytora kodu, te ustawienia są utrwalane w formacie XML i automatycznie odczytywać do pamięci w czasie wykonywania.  
  
 Aby uzyskać szczegółowe informacje dotyczące korzystania z tych funkcji zobacz poniższe tematy Pomocy.  
  
|Do|Zobacz|  
|--------|---------|  
|Użyj <xref:System.Windows.Forms.BindingSource> składnika|[Instrukcje: powiązywanie kontrolek formularzy Windows Forms ze składnikiem BindingSource przy użyciu narzędzia Projektant](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Praca z [!INCLUDE[vstecado](~/includes/vstecado-md.md)] źródeł danych|[Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Korzystanie z okna źródeł danych|[Wskazówki: Wyświetlanie danych w formularzu systemu Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Wdrażanie aplikacji na komputerach klienckich  
 Po napisano aplikację, konieczne jest wysłanie go do użytkowników, aby mogli zainstalować i uruchom go na komputerach klienckich. Przy użyciu [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] technologii, można wdrożyć aplikacji z poziomu programu Visual Studio za pomocą kilku kliknięć i udostępnić użytkownikowi adres URL aplikacji sieci Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] zarządza wszystkie elementy i zależności aplikacji i zapewnia, że aplikacja jest poprawnie zainstalowana na komputerze klienckim.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacje mogą być skonfigurowane do uruchamiania tylko wtedy, gdy użytkownik jest połączony z siecią lub uruchom oba projekty w trybie online i offline. Po określeniu, czy aplikacja powinna obsługiwać operacji w trybie offline, [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] dodaje łącze do aplikacji w użytkownika **Start** menu, dzięki czemu użytkownik może go otwierać bez korzystania z adresu URL.  
  
 Podczas aktualizacji aplikacji opublikowaniu nowego manifest wdrażania i nową kopię aplikacji do serwera sieci Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] wykrywa, że nie jest dostępna aktualizacja i uaktualnia użytkownika instalacji; żadne Programowanie niestandardowych jest wymagana w celu zaktualizowania starego zestawy.  
  
 Aby uzyskać pełne wprowadzenie do [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowe informacje dotyczące korzystania z tych funkcji zobacz następujące tematy pomocy:  
  
|Do|Zobacz|  
|--------|---------|  
|Wdróż aplikację z [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizacja [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] wdrożenia|[Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Zarządzanie zabezpieczeniami z [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Inne formanty i funkcje  
 Istnieje wiele innych funkcji w formularzach systemu Windows, która implementującej typowych zadań, szybkie i łatwe, takie jak obsługa tworzenie okien dialogowych, drukowanie, dodawanie pomocy i dokumentacja i lokalizacja aplikacji na wiele języków. Ponadto formularzy systemu Windows opiera się na skuteczną ochronę systemu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], dzięki któremu można zwolnić większe bezpieczeństwo aplikacji dla klientów.  
  
 Aby uzyskać szczegółowe informacje dotyczące korzystania z tych funkcji zobacz następujące tematy pomocy:  
  
|Do|Zobacz|  
|--------|---------|  
|Drukuj zawartość formularza|[Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Dowiedz się więcej na temat zabezpieczenia formularzy systemu Windows|[Przegląd zabezpieczeń w formularzach Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Windows Forms — omówienie](../../../framework/winforms/windows-forms-overview.md)  
 [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
