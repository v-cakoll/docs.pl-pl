---
title: Przegląd dostawców automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1f780ffc37b0aff93a3358c1980d271fe10c1321
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179877"
---
# <a name="ui-automation-providers-overview"></a>Przegląd dostawców automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Dostawcy automatyzacji interfejsu użytkownika umożliwiają formanty do komunikowania się z aplikacjami klienckimi automatyzacji interfejsu użytkownika. Ogólnie rzecz biorąc każdy formant [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub inny element odrębny w a jest reprezentowany przez dostawcę. Dostawca udostępnia informacje o elemencie i opcjonalnie implementuje wzorce kontroli, które umożliwiają aplikacji klienckiej do interakcji z formantem.  
  
 Aplikacje klienckie zwykle nie muszą pracować bezpośrednio z dostawcami. Większość standardowych formantów w aplikacjach korzystających z [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] systemu Win32, Windows [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Forms lub frameworks są automatycznie udostępniane systemowi. Aplikacje, które implementują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] formanty niestandardowe mogą również implementować dostawców dla tych formantów, a aplikacje klienckie nie muszą podejmować żadnych specjalnych kroków, aby uzyskać do nich dostęp.  
  
 W tym temacie przedstawiono omówienie sposobu implementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez deweloperów kontroli dostawców, szczególnie w przypadku formantów w formularzach systemu Windows i oknach systemu Win32.  
  
<a name="Types_of_Providers"></a>
## <a name="types-of-providers"></a>Rodzaje dostawców  
 Dostawcy automatyzacji interfejsu użytkownika dzielą się na dwie kategorie: dostawców po stronie klienta i dostawców po stronie serwera.  
  
### <a name="client-side-providers"></a>Dostawcy po stronie klienta  
 Dostawcy po stronie klienta są implementowane przez klientów automatyzacji interfejsu użytkownika do komunikowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]się z aplikacją, która nie obsługuje lub nie obsługuje w pełni, . Dostawcy po stronie klienta zwykle komunikują się z serwerem w granicach procesu, wysyłając i odbierając wiadomości systemu Windows.  
  
 Ponieważ dostawcy automatyzacji interfejsu użytkownika dla formantów [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] w systemie Win32, Windows Forms lub aplikacje są dostarczane jako część systemu operacyjnego, aplikacje klienckie rzadko muszą implementować własnych dostawców, a ten przegląd nie obejmuje ich dalej.  
  
### <a name="server-side-providers"></a>Dostawcy po stronie serwera  
 Dostawcy po stronie serwera są implementowani przez formanty niestandardowe lub aplikacje oparte na [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]platformie interfejsu użytkownika innej niż Win32, Windows Forms lub .  
  
 Dostawcy po stronie serwera komunikują się z aplikacjami klienckimi w granicach procesu, ujawniając interfejsy w systemie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowym, który z kolei obsługuje żądania od klientów.  
  
<a name="AutomationProviderConcepts"></a>
## <a name="ui-automation-provider-concepts"></a>Pojęcia dotyczące automatyzacji interfejsu użytkownika  
 Ta sekcja zawiera krótkie wyjaśnienia niektórych kluczowych pojęć, które należy zrozumieć w celu zaimplementowania dostawców automatyzacji interfejsu użytkownika.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy, które są widoczne dla klientów automatyzacji interfejsu użytkownika. Przykłady obejmują okna aplikacji, okienka, przyciski, etykietki narzędzi, pola listy i elementy listy.  
  
### <a name="navigation"></a>Nawigacja  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są narażone na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientów jako drzewo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]konstruuje drzewo, przechodząc z jednego elementu do drugiego. Nawigacja jest włączona przez dostawców dla każdego elementu, z których każdy może wskazywać na element nadrzędny, rodzeństwo i elementy podrzędne.  
  
 Aby uzyskać więcej informacji na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temat widoku klienta drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Widoki  
 Klient może zobaczyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo w trzech widokach głównych, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Widok nieprzetworzony|Zawiera wszystkie elementy.|  
|Widok sterowania|Zawiera elementy, które są formantami.|  
|Widok zawartości|Zawiera elementy, które mają zawartość.|  
  
 Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat widoków klienta drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
 Jest odpowiedzialny za implementacji dostawcy do definiowania elementu jako element zawartości lub elementu sterującego. Elementy sterujące mogą lub nie mogą być również elementami zawartości, ale wszystkie elementy zawartości są elementami sterującymi.  
  
### <a name="frameworks"></a>Struktury  
 Struktura jest składnikiem, który zarządza formanty podrzędnych, testowania trafień i renderowania w obszarze ekranu. Na przykład okno Win32, często określane jako HWND, może służyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jako framework, który zawiera wiele elementów, takich jak pasek menu, pasek stanu i przyciski.  
  
 Formanty kontenera Win32, takie jak pola listy i widoki drzewa są uważane za struktury, ponieważ zawierają własny kod do renderowania elementów podrzędnych i przeprowadzania testów trafień na nich. Z drugiej [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] strony pole listy nie jest strukturą, ponieważ renderowanie i testowanie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] trafień jest obsługiwane przez okno zawierające.  
  
 W [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikacji mogą być składa się z różnych struktur. Na przykład okno aplikacji HWND może zawierać dynamiczny kod HTML (DHTML), który z kolei zawiera składnik, taki jak pole kombi w HWND.  
  
### <a name="fragments"></a>Fragments  
 Fragment jest kompletnym poddrzewem elementów z określonej struktury. Element w węźle głównym poddrzewa jest nazywany katalogiem głównym fragmentu. Katalog główny fragmentu nie ma nadrzędnego, ale jest obsługiwany w innej ramach, zwykle w oknie Win32 (HWND).  
  
### <a name="hosts"></a>Hosts  
 Węzeł główny każdego fragmentu musi być obsługiwany w elemencie, zwykle w oknie Win32 (HWND). Wyjątkiem jest pulpit, który nie jest obsługiwany w żadnym innym elemencie. Host formantu niestandardowego jest HWND samego formantu, a nie okno aplikacji lub inne okno, które może zawierać grupy formantów najwyższego poziomu.  
  
 Host fragmentu odgrywa ważną rolę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w świadczeniu usług. Umożliwia nawigację do katalogu głównego fragmentu i dostarcza niektóre właściwości domyślne, dzięki czemu dostawca niestandardowy nie musi ich implementować.  
  
## <a name="see-also"></a>Zobacz też

- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
