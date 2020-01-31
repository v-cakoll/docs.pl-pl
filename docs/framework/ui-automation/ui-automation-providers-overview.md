---
title: Przegląd dostawców automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 98208f1e1fa1b540bf3880e33478854128505233
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778787"
---
# <a name="ui-automation-providers-overview"></a>Przegląd dostawców automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Dostawcy automatyzacji interfejsu użytkownika umożliwiają kontrolowanie komunikacji z aplikacjami klienckimi automatyzacji interfejsu użytkownika. Ogólnie rzecz biorąc każda kontrolka lub inny odrębny element w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] jest reprezentowany przez dostawcę. Dostawca ujawnia informacje o elemencie i opcjonalnie implementuje wzorce kontroli, które umożliwiają aplikacji klienckiej współpracującie z kontrolką.  
  
 Aplikacje klienckie zazwyczaj nie muszą bezpośrednio współpracować z dostawcami. Większość standardowych kontrolek w aplikacjach korzystających z Win32, Windows Forms lub [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] Framework są automatycznie uwidaczniane dla systemu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Aplikacje implementujące niestandardowe kontrolki mogą również implementować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców dla tych kontrolek, a aplikacje klienckie nie muszą podejmować żadnych specjalnych kroków w celu uzyskania dostępu do nich.  
  
 Ten temat zawiera omówienie sposobu, w jaki deweloperzy kontroli implementują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców, szczególnie w przypadku formantów w Windows Forms i Windows Win32.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy dostawców  
 Dostawcy automatyzacji interfejsu użytkownika dzielą się na dwie kategorie: dostawcy po stronie klienta i dostawcy po stronie serwera.  
  
### <a name="client-side-providers"></a>Dostawcy po stronie klienta  
 Dostawcy po stronie klienta są implementowani przez klientów automatyzacji interfejsu użytkownika do komunikowania się z aplikacją, która nie obsługuje lub nie obsługuje w pełni [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Dostawcy po stronie klienta zazwyczaj komunikują się z serwerem przez granicę procesu przez wysyłanie i otrzymywanie komunikatów systemu Windows.  
  
 Ponieważ dostawcy automatyzacji interfejsu użytkownika dla formantów w Win32, Windows Forms lub aplikacje [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] są dostarczane jako część systemu operacyjnego, aplikacje klienckie rzadko muszą implementować swoich własnych dostawców i nie obejmują ich jeszcze więcej.  
  
### <a name="server-side-providers"></a>Dostawcy po stronie serwera  
 Dostawcy po stronie serwera są implementowani przez niestandardowe kontrolki lub aplikacje oparte na środowisku interfejsu użytkownika innym niż Win32, Windows Forms lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostawcy po stronie serwera komunikują się z aplikacjami klienckimi na granicy procesu przez udostępnienie interfejsów do systemu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core, który z kolei obsługuje żądania od klientów.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Pojęcia dotyczące dostawcy automatyzacji interfejsu użytkownika  
 Ta sekcja zawiera krótkie objaśnienia niektórych kluczowych pojęć, które należy zrozumieć w celu wdrożenia dostawców automatyzacji interfejsu użytkownika.  
  
### <a name="elements"></a>Elementy  
 elementy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] są częścią [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], które są widoczne dla klientów automatyzacji interfejsu użytkownika. Przykłady obejmują okna aplikacji, okienka, przyciski, etykietki narzędzi, pola listy i elementy listy.  
  
### <a name="navigation"></a>Nawigacja  
 elementy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] są dostępne dla klientów jako drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] konstruuje drzewo, przechodząc od jednego elementu do drugiego. Nawigacja jest włączana przez dostawców dla każdego elementu, z których każdy może wskazywać element nadrzędny, elementy równorzędne i elementy podrzędne.  
  
 Aby uzyskać więcej informacji na temat widoku klienta drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Widoki  
 Klient może zobaczyć drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w trzech głównych widokach, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Widok nieprzetworzony|Zawiera wszystkie elementy.|  
|Widok kontrolki|Zawiera elementy, które są kontrolkami.|  
|Widok Zawartość|Zawiera elementy, które mają zawartość.|  
  
 Aby uzyskać więcej informacji o widokach klienta drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
 Jest odpowiedzialna za implementację dostawcy, aby zdefiniować element jako element zawartości lub element kontrolny. Elementy kontrolne mogą być również elementami zawartości, ale wszystkie elementy zawartości są elementami kontrolnymi.  
  
### <a name="frameworks"></a>Struktury  
 Platforma jest składnikiem, który zarządza kontrolkami podrzędnymi, testowaniem trafień i renderowaniem w obszarze ekranu. Na przykład okno Win32, często określane jako HWND, może stanowić strukturę, która zawiera wiele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, takich jak pasek menu, pasek stanu i przyciski.  
  
 Formanty kontenera Win32, takie jak pola list i widoki drzewa, są uznawane za struktury, ponieważ zawierają własny kod do renderowania elementów podrzędnych i wykonujących na nich Testy trafień. Z kolei pole listy [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] nie jest strukturą, ponieważ renderowanie i testowanie trafień jest obsługiwane przez okno zawierające [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w aplikacji może składać się z różnych platform. Na przykład okno aplikacji HWND może zawierać dynamiczny kod HTML (DHTML), który z kolei zawiera składnik, taki jak pole kombi w elemencie HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Fragment to kompletny poddrzewo elementów z określonej struktury. Element w węźle głównym poddrzewa jest nazywany korzeniem fragmentu. Katalog główny fragmentu nie ma elementu nadrzędnego, ale jest hostowany w obrębie innej struktury, zazwyczaj okna Win32 (HWND).  
  
### <a name="hosts"></a>Hosty  
 Węzeł główny każdego fragmentu musi być hostowany w elemencie, zazwyczaj okno Win32 (HWND). Wyjątkiem są komputery stacjonarne, które nie są hostowane w żadnym innym elemencie. Host kontrolki niestandardowej jest elementem HWND samego formantu, a nie oknem aplikacji ani innym oknem, które może zawierać grupy formantów najwyższego poziomu.  
  
 Host fragmentu odgrywa ważną rolę w dostarczaniu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usług. Umożliwia nawigowanie do głównego fragmentu i udostępnia niektóre właściwości domyślne, aby nie zaimplementował dostawcy niestandardowego.  
  
## <a name="see-also"></a>Zobacz także

- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
