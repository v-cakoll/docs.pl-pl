---
title: Formularze systemu Windows — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 50c88aec8ac57be2ab317ac91464d68503607738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541729"
---
# <a name="windows-forms-overview"></a>Formularze systemu Windows — Omówienie
Poniższy przegląd zawiera omówienie zalet inteligentnych aplikacji klienckich, główne funkcje programowania formularzy systemu Windows i jak formularze systemu Windows umożliwia inteligentne klientów, którzy wymagań przedsiębiorstwa i użytkownicy końcowi bieżącej kompilacji.  
  
## <a name="windows-forms-and-smart-client-applications"></a>Formularze systemu Windows i inteligentnych aplikacji klienckich  
 Windows Forms opracowywania inteligentne klientów. *Inteligentne klientów* Bogato aplikacje, które ułatwiają wdrażanie i aktualizacji, można pracować, gdy są one połączone z lub odłączony od Internetu, a dostęp do zasobów na komputerze lokalnym w bardziej bezpieczny sposób niż tradycyjne Aplikacje systemu Windows.  
  
### <a name="building-rich-interactive-user-interfaces"></a>Tworzenie interfejsów użytkownika rozbudowanych, interakcyjnych  
 Formularze systemu Windows jest technologią klienta inteligentnego [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], zbiór bibliotek zarządzanych, które upraszczają typowych zadań aplikacji, takich jak odczytywanie i zapisywanie w systemie plików. Gdy używasz Środowisko deweloperskie, takimi jak Visual Studio, można utworzyć aplikacji inteligentnych klientów formularzy systemu Windows, które zawierają informacje, żądać danych wejściowych od użytkowników i komunikować się ze zdalnymi komputerami za pośrednictwem sieci.  
  
 W formularzach systemu Windows *formularza* jest visual powierzchni, na którym można wyświetlić informacje dla użytkownika. Zwykle w przypadku tworzenia aplikacji formularzy systemu Windows, dodawanie formantów do formularzy i opracowując odpowiedzi na działania użytkownika, takie jak kliknięcie myszą lub naciśnięcie klucza. A *kontroli* jest elementem interfejsu odrębny użytkownika, który wyświetla dane lub akceptuje dane wejściowe.  
  
 Gdy użytkownik wykona coś do formularza lub jednego z jego formantów, akcja generuje zdarzenie. Aplikacja reaguje na zdarzenia te przy użyciu kodu i przetwarza zdarzenia wystąpieniach. Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
 Formularze systemu Windows zawiera różne formantów, które można dodać do formularzy: formanty zawierające pola tekstowe, przycisków rozwijanych, przyciski radiowe i nawet stron sieci Web. Aby uzyskać listę wszystkich kontrolek, można użyć w formularzu, zobacz [formanty do użycia w formularzach systemu Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli formant nie spełnia Twoje potrzeby, formularze systemu Windows obsługuje także tworzenie własnych niestandardowych formantów przy użyciu <xref:System.Windows.Forms.UserControl> klasy.  
  
 Formularze systemu Windows ma sformatowanego kontrolek interfejsu użytkownika, które emulują funkcje wysokiej jakości aplikacji, takich jak Microsoft Office. Jeśli używasz <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip> formantu, można utworzyć paski narzędzi i menu, które zawierają tekst i obrazy, wyświetlania podmenu i udostępniać inne formanty, takie jak pola tekstowe i pola kombi.  
  
 Projektant formularzy systemu Windows przeciągania i upuszczania programu Visual Studio umożliwia łatwe tworzenie aplikacji formularzy systemu Windows. Po prostu zaznacz formantów kursor i Dodaj miejsce w formularzu. Projektant udostępnia narzędzia, takie jak linie siatki i przystawki wierszy do wykonania proste poza wyrównywanie formantów. Czy za pomocą programu Visual Studio lub kompilacji w wierszu polecenia, można użyć <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.SplitContainer> służy do tworzenia zaawansowanych tworzą układów w krótszym czasie.  
  
 Na koniec, jeśli musisz utworzyć własne niestandardowe elementy interfejsu użytkownika <xref:System.Drawing> przestrzeń nazw zawiera dużej liczby klas do renderowania linii, okręgi i innych kształtów bezpośrednio na formularzu.  
  
> [!NOTE]
>  Formanty formularzy systemu Windows nie mają być przekazywane między domenami aplikacji. Z tego powodu nie obsługuje przekazywanie przez formant formularzy systemu Windows <xref:System.AppDomain> granic, nawet jeśli <xref:System.Windows.Controls.Control> podstawowy typ <xref:System.MarshalByRefObject> może wskazywać, że jest to możliwe. Aplikacji formularzy systemu Windows, które mają kilka domen aplikacji są obsługiwane, dopóki nie formanty formularzy systemu Windows są przekazywane przez granice domeny aplikacji.  
  
#### <a name="help-creating-forms-and-controls"></a>Uzyskać pomoc przy tworzeniu formularzy i kontrolek  
 Aby uzyskać szczegółowe informacje na temat używania tych funkcji zobacz poniższe tematy Pomocy.  
  
|Opis|Temat pomocy|  
|-----------------|----------------|  
|Za pomocą formantów na formularzach|[Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|Przy użyciu <xref:System.Windows.Forms.ToolStrip> formantu|[Instrukcje: tworzenie podstawowych kontrolek ToolStrip z elementami standardowymi przy użyciu narzędzia Projektant](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|Tworzenie grafiki <xref:System.Drawing>|[Wprowadzenie do programowania grafiki](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Tworzenie niestandardowych formantów|[Instrukcje: dziedziczenie z klasy UserControl](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### <a name="displaying-and-manipulating-data"></a>Wyświetlanie danych i operowanie nimi  
 Wiele aplikacji musi zawierać dane z bazy danych, plik XML, usługi XML sieci Web lub innego źródła danych. Formularze systemu Windows udostępnia elastyczną kontrolę, o nazwie <xref:System.Windows.Forms.DataGridView> formantu do wyświetlania tych danych tabelarycznych w tradycyjnych formacie wiersz i kolumnę, tak, aby każdy element danych zajmuje komórki. Jeśli używasz <xref:System.Windows.Forms.DataGridView>, można dostosować wygląd pojedynczych komórek, blokuje dowolnego wierszy i kolumn w oraz wyświetlanie formantów złożonych wewnątrz komórek, między innymi funkcjami.  
  
 Łączenie ze źródłami danych w sieci jest prostym zadaniem z klientami inteligentne formularzy systemu Windows. <xref:System.Windows.Forms.BindingSource> Składnika nowych z formularzy systemu Windows w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]reprezentuje połączenie ze źródłem danych i opisuje metody powiązanie danych z formantami, przechodząc do poprzedniego i następnego rekordów, edytowanie rekordów i zapisywanie zmian z powrotem do oryginalnego źródła. <xref:System.Windows.Forms.BindingNavigator> Kontroli udostępnia prosty interfejs w porównaniu z <xref:System.Windows.Forms.BindingSource> składnika użytkownikom przechodzenie między rekordów.  
  
 Formanty powiązane z danymi można łatwo utworzyć przy użyciu okna źródeł danych. Jest wyświetlany w oknie źródeł danych, takich jak bazy danych, usługi sieci Web i obiektów w projekcie. Formanty powiązane z danymi można utworzyć, przeciągając elementy z tego okna na formularze w projekcie. Użytkownik może również wiązania danych istniejących formantów do danych przeciągając obiekty z okna źródeł danych na istniejące kontrolki.  
  
 Jest innego typu powiązania danych w formularzach systemu Windows można zarządzać *ustawienia*. Większość inteligentnych aplikacji klienckich należy zachować pewne informacje o ich stanu czasu wykonywania, takich jak rozmiar Ostatnia znana formularzy i zachować dane preferencji użytkownika, takie jak domyślne lokalizacje zapisane pliki. Funkcja ustawienia aplikacji adresy te wymagania, zapewniając łatwy sposób przechowywania obu typów ustawień na komputerze klienckim. Po zdefiniowaniu te ustawienia przy użyciu programu Visual Studio lub edytora kodu, ustawienia są utrwalone w formacie XML i automatycznie odczytywać do pamięci w czasie wykonywania.  
  
#### <a name="help-displaying-and-manipulating-data"></a>Wyświetlanie pomocy i operowanie nimi danych  
 Aby uzyskać szczegółowe informacje na temat używania tych funkcji zobacz poniższe tematy Pomocy.  
  
|Opis|Temat pomocy|  
|-----------------|----------------|  
|Przy użyciu <xref:System.Windows.Forms.BindingSource> składnika|[Instrukcje: powiązywanie kontrolek formularzy Windows Forms ze składnikiem BindingSource przy użyciu narzędzia Projektant](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Praca z [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] źródeł danych|[Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|Korzystanie z okna źródeł danych|[Wskazówki: Wyświetlanie danych w formularzu systemu Windows](http://msdn.microsoft.com/library/f6e08c2c-c792-43de-adf3-3e52c0100225)|  
|Przy użyciu ustawień aplikacji|[Instrukcje: tworzenie ustawień aplikacji](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### <a name="deploying-applications-to-client-computers"></a>Wdrażanie aplikacji na komputerach klienckich  
 Po napisano aplikację, musisz wysłać aplikacji dla użytkowników, aby mogli zainstalować i uruchom go na komputerach klienckich. Jeśli używasz [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologii, można wdrożyć aplikacji z poziomu programu Visual Studio za pomocą kilku kliknięć i zapewnić użytkownikom adres URL aplikacji sieci Web. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] zarządza wszystkie elementy i zależności w aplikacji oraz zapewnia, że aplikacja jest poprawnie zainstalowana na komputerze klienckim.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikacje mogą być skonfigurowane do uruchamiania tylko wtedy, gdy użytkownik jest połączony z siecią lub uruchom oba projekty w trybie online i offline. Po określeniu, czy aplikacja powinna obsługiwać operacji w trybie offline, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dodaje łącze do aplikacji w użytkownika **Start** menu. Użytkownik może następnie otwórz aplikację bez korzystania z adresu URL.  
  
 Podczas aktualizacji aplikacji opublikowaniu nowego manifest wdrażania i nową kopię aplikacji do serwera sieci Web. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wykryje, że jest dostępna aktualizacja i Uaktualnij Instalacja dla użytkownika; żadne Programowanie niestandardowych jest wymagana w celu zaktualizowania starego zestawy.  
  
#### <a name="help-deploying-clickonce-applications"></a>Pomoc wdrażanie technologii ClickOnce  
 Aby uzyskać pełne wprowadzenie do [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment). Aby uzyskać szczegółowe informacje na temat używania tych funkcji zobacz następujące tematy pomocy  
  
|Opis|Temat pomocy|  
|-----------------|----------------|  
|Wdrażanie aplikacji przy użyciu [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizowanie [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożenia|[Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Zarządzanie zabezpieczeniami za pomocą [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
### <a name="other-controls-and-features"></a>Inne formanty i funkcje  
 Istnieje wiele innych funkcji w formularzach systemu Windows, która implementującej typowych zadań, szybkie i łatwe, takie jak obsługa tworzenie okien dialogowych, drukowanie, dodawanie pomocy i dokumentacja i lokalizacja aplikacji na wiele języków. Ponadto formularzy systemu Windows opiera się na skuteczną ochronę systemu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Z tym systemem można zwolnić większe bezpieczeństwo aplikacji dla klientów.  
  
#### <a name="help-implementing-other-controls-and-features"></a>Implementowanie inne formanty i funkcje pomocy  
 Aby uzyskać szczegółowe informacje na temat używania tych funkcji zobacz poniższe tematy Pomocy.  
  
|Opis|Temat pomocy|  
|-----------------|----------------|  
|Drukowanie zawartość formularza|[Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|Dowiedz się więcej na temat zabezpieczenia formularzy systemu Windows|[Przegląd zabezpieczeń w formularzach Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do formularzy Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Tworzenie nowego formularza systemu Windows](../../../docs/framework/winforms/creating-a-new-windows-form.md)  
 [ToolStrip, kontrolka — omówienie](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [DataGridView, kontrolka — omówienie](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [BindingSource, składnik — omówienie](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
