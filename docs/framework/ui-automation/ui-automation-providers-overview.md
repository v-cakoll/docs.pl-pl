---
title: Przegląd dostawców automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: c8db2e6cbd1f0c0dd61ecb8e147133b8c608ea8f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042041"
---
# <a name="ui-automation-providers-overview"></a>Przegląd dostawców automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Dostawcy automatyzacji interfejsu użytkownika umożliwiają kontrolowanie komunikacji z aplikacjami klienckimi automatyzacji interfejsu użytkownika. Ogólnie rzecz biorąc każda kontrolka lub inny odrębny element [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] w jest reprezentowany przez dostawcę. Dostawca ujawnia informacje o elemencie i opcjonalnie implementuje wzorce kontroli, które umożliwiają aplikacji klienckiej współpracującie z kontrolką.  
  
 Aplikacje klienckie zazwyczaj nie muszą bezpośrednio współpracować z dostawcami. Większość standardowych kontrolek w aplikacjach korzystających [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]z, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], lub [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] struktur są automatycznie uwidaczniane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w systemie. Aplikacje implementujące niestandardowe kontrolki mogą również [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] implementować dostawców dla tych kontrolek, a aplikacje klienckie nie muszą podejmować żadnych specjalnych kroków w celu uzyskania dostępu do nich.  
  
 Ten temat zawiera omówienie sposobu, w jaki deweloperzy kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] implementują dostawców, szczególnie w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] przypadku [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] formantów w i Windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy dostawców  
 Dostawcy automatyzacji interfejsu użytkownika dzielą się na dwie kategorie: dostawcy po stronie klienta i dostawcy po stronie serwera.  
  
### <a name="client-side-providers"></a>Dostawcy po stronie klienta  
 Dostawcy po stronie klienta są implementowani przez klientów automatyzacji interfejsu użytkownika do komunikowania się z aplikacją, która nie obsługuje lub nie jest w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pełni obsługiwana. Dostawcy po stronie klienta zazwyczaj komunikują się z serwerem przez granicę procesu przez wysyłanie i otrzymywanie komunikatów systemu Windows.  
  
 Ponieważ dostawcy automatyzacji interfejsu użytkownika dla kontrolek w programie [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikacje są dostarczane jako część systemu operacyjnego, aplikacje klienckie rzadko muszą implementować własnych dostawców i nie obejmują ich celu.  
  
### <a name="server-side-providers"></a>Dostawcy po stronie serwera  
 Dostawcy po stronie serwera są implementowani przez niestandardowe kontrolki lub aplikacje oparte na strukturze interfejsu użytkownika innym niż [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms lub. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]  
  
 Dostawcy po stronie serwera komunikują się z aplikacjami klienckimi na granicy procesu przez udostępnienie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsów do systemu podstawowego, co z kolei obsługuje żądania od klientów.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Pojęcia dotyczące dostawcy automatyzacji interfejsu użytkownika  
 Ta sekcja zawiera krótkie objaśnienia niektórych kluczowych pojęć, które należy zrozumieć w celu wdrożenia dostawców automatyzacji interfejsu użytkownika.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementami, które są widoczne dla klientów automatyzacji interfejsu użytkownika. Przykłady obejmują okna aplikacji, okienka, przyciski, etykietki narzędzi, pola listy i elementy listy.  
  
### <a name="navigation"></a>Nawigacja  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są udostępniane klientom jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]konstruuje drzewo, przechodząc od jednego elementu do drugiego. Nawigacja jest włączana przez dostawców dla każdego elementu, z których każdy może wskazywać element nadrzędny, elementy równorzędne i elementy podrzędne.  
  
 Aby uzyskać więcej informacji na temat widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Widoki  
 Klient może zobaczyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo w trzech głównych widokach, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Widok nieprzetworzony|Zawiera wszystkie elementy.|  
|Widok kontrolki|Zawiera elementy, które są kontrolkami.|  
|Widok zawartości|Zawiera elementy, które mają zawartość.|  
  
 Aby uzyskać więcej informacji na temat widoków [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta w drzewie, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
 Jest odpowiedzialna za implementację dostawcy, aby zdefiniować element jako element zawartości lub element kontrolny. Elementy kontrolne mogą być również elementami zawartości, ale wszystkie elementy zawartości są elementami kontrolnymi.  
  
### <a name="frameworks"></a>Struktury  
 Platforma jest składnikiem, który zarządza kontrolkami podrzędnymi, testowaniem trafień i renderowaniem w obszarze ekranu. Na przykład [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okno, często określane jako właściwość HWND, może stanowić strukturę, która zawiera wiele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, takich jak pasek menu, pasek stanu i przyciski.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]formanty kontenera, takie jak pola list i widoki drzewa, są uznawane za struktury, ponieważ zawierają własny kod do renderowania elementów podrzędnych i wykonujących na nich Testy trafień. Z kolei [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pole listy nie jest strukturą, ponieważ renderowanie i testowanie trafień jest obsługiwane przez okno zawierające [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] W aplikacji może być składają się z różnych platform. Na przykład okno aplikacji HWND może zawierać dynamiczny kod HTML (DHTML), który z kolei zawiera składnik, taki jak pole kombi w elemencie HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Fragment to kompletny poddrzewo elementów z określonej struktury. Element w węźle głównym poddrzewa jest nazywany korzeniem fragmentu. Katalog główny fragmentu nie ma elementu nadrzędnego, ale jest hostowany w obrębie innej struktury, zazwyczaj [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okna (HWND).  
  
### <a name="hosts"></a>Pracując  
 Węzeł główny każdego fragmentu musi być hostowany w elemencie, zazwyczaj [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] w oknie (HWND). Wyjątkiem są komputery stacjonarne, które nie są hostowane w żadnym innym elemencie. Host kontrolki niestandardowej jest elementem HWND samego formantu, a nie oknem aplikacji ani innym oknem, które może zawierać grupy formantów najwyższego poziomu.  
  
 Host fragmentu odgrywa ważną rolę w świadczeniu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usług. Umożliwia nawigowanie do głównego fragmentu i udostępnia niektóre właściwości domyślne, aby nie zaimplementował dostawcy niestandardowego.  
  
## <a name="see-also"></a>Zobacz także

- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
