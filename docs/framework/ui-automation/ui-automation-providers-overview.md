---
title: Przegląd dostawców automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7b4286abdb2e2b5bb3f91f6fa0bbffd6beda8efc
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580204"
---
# <a name="ui-automation-providers-overview"></a>Przegląd dostawców automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Dostawcy automatyzacji interfejsu użytkownika włączyć formanty do komunikacji przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich. Ogólne, każdy formant lub inny element distinct w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] jest reprezentowany przez dostawcę. Dostawca udostępnia informacji na temat elementu i opcjonalnie implementuje wzorców kontrolek, które umożliwiają aplikacji klienckiej wchodzić w interakcje z kontrolką.  
  
 Aplikacje klienckie zwykle trzeba pracować bezpośrednio z dostawców. Większość standardowych kontrolek w aplikacji, które używają [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], lub [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] struktury są automatycznie widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systemu. Aplikacje, które implementują niestandardowe formanty mogą także implementować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców dla tych formantów i aplikacji klienckich nie trzeba podjąć specjalne kroki, aby uzyskać do nich dostęp.  
  
 Ten temat zawiera omówienie sposób implementacji kontroli deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców, szczególnie w przypadku kontrolek w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] systemu windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy dostawców  
 Dostawcy automatyzacji interfejsu użytkownika można podzielić na dwie kategorie: dostawcy po stronie klienta i dostawcy po stronie serwera.  
  
### <a name="client-side-providers"></a>Dostawcy po stronie klienta  
 Dostawcy po stronie klienta są implementowane przez klientów automatyzacji interfejsu użytkownika do komunikowania się z aplikacją, która nie obsługuje lub nie obsługuje w pełni, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Dostawcy po stronie klienta zazwyczaj komunikacji z serwerem przez granicę procesu przez wysyłanie i odbieranie komunikatów Windows.  
  
 Ponieważ dostawców automatyzacji interfejsu użytkownika dla kontrolek w [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikacje są dostarczane jako część systemu operacyjnego, aplikacje klienckie rzadko musiał zostać zaimplementowany własnych dostawców i w tym omówieniu nie obejmują ich bardziej szczegółowo.  
  
### <a name="server-side-providers"></a>Dostawcy po stronie serwera  
 Dostawcy po stronie serwera są implementowane przez formanty niestandardowe lub aplikacje, które zależą od struktury interfejsu użytkownika inne niż [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostawcy po stronie serwera komunikować się przy użyciu aplikacji klienckich przez granicę procesu uwidaczniając interfejsy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core system, który z kolei obsługują żądania od klientów.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Pojęcia dotyczące dostawcy automatyzacji interfejsu użytkownika  
 Ta sekcja zawiera krótkie objaśnienia niektóre kluczowe założenia, które należy zrozumieć w celu wdrożenia dostawców automatyzacji interfejsu użytkownika.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy są fragmenty [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , które są widoczne dla klientów automatyzacji interfejsu użytkownika. Przykładami aplikacji systemu windows, okienka, przyciski, etykietki narzędzi, pola listy i elementy listy.  
  
### <a name="navigation"></a>Nawigacja  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy są widoczne dla klientów jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tworzy drzewo, przechodząc od jednego elementu na inny. Nawigacja jest włączona przez dostawców dla każdego elementu, z których każdy może wskazywać elementu nadrzędnego, elementów równorzędnych i elementy podrzędne.  
  
 Aby uzyskać więcej informacji, w widoku klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Widoki  
 Klienta można zobaczyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa w trzech głównych widoków, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Nieprzetworzony widok|Zawiera wszystkie elementy.|  
|Formant widoku|Zawiera elementy, będących kontrolkami.|  
|Widok zawartości|Zawiera elementy, które mają zawartość.|  
  
 Więcej informacji na temat widoków klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Jest odpowiedzialny za implementacja dostawcy, aby zdefiniować element jako element zawartości lub element kontroli. Elementy kontroli może lub nie może także dopuszczać elementów zawartości, ale wszystkie elementy zawartości są elementy kontroli.  
  
### <a name="frameworks"></a>Struktury  
 Struktura jest składnikiem, który zarządza formantów podrzędnych, testowanie trafień i renderowanie w obszarze ekranu. Na przykład [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okna, często nazywane HWND, może służyć jako struktura, która zawiera wiele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, takich jak pasek menu, pasek stanu i przyciski.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] Określa kontener, takich jak pola listy i widok drzewa są uznawane za struktur, ponieważ zawierają one swój własny kod do renderowania elementów podrzędnych i przeprowadzania testowania trafień na nich. Z drugiej strony [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pola listy nie jest to struktura, ponieważ renderowania i testowanie trafień jest obsługiwane przez zawierający [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w aplikacji może składać się z różnych platform. Na przykład może zawierać okno aplikacji HWND [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] który z kolei zawiera składnika, takiego jak pole kombi w HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Określony fragment jest pełne poddrzewo elementów z określonej struktury. Element w węźle głównym poddrzewo jest nazywany elementem głównym fragmentu. Katalog główny fragment nie ma elementu nadrzędnego, ale hostowanych w ramach innych struktury [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okna (HWND).  
  
### <a name="hosts"></a>Hosty  
 Węzeł główny każdego fragmentu musi być hostowany w elemencie, zwykle [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okna (HWND). Wyjątek stanowi pulpitu, który nie znajduje się w innym elemencie. Host formantu niestandardowego jest HWND samego formantu, nie w oknie aplikacji lub inne okno, które mogą zawierać grup formantów najwyższego poziomu.  
  
 Host fragmentu odgrywa ważną rolę w dostarczaniu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usług. Umożliwia nawigacji do fragmentu katalogu głównego i dostarcza niektórych właściwości domyślne tak, aby niestandardowego dostawcy nie trzeba ich wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
