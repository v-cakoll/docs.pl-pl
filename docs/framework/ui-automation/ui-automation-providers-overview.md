---
title: "Przegląd dostawców automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dc5cb5749bbfe06fd3a1bbe3537b28c7bbfa295d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-providers-overview"></a>Przegląd dostawców automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Dostawcy automatyzacji interfejsu użytkownika Włącz formanty do komunikowania się z aplikacjami klienckimi automatyzacji interfejsu użytkownika. Ogólne, każdej kontrolki lub distinct element [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] jest reprezentowany przez dostawcę. Przedstawia informacje o elemencie i opcjonalnie implementuje kontroli wzorców, które umożliwiają aplikacji klienta do interakcji z formantem dostawcy.  
  
 Aby pracować bezpośrednio z dostawców nie masz zwykle aplikacji klienckich. Większość standardowych formantów w aplikacjach używających [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], lub [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] struktury są automatycznie widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systemu. Aplikacje, które implementują Kontrolki niestandardowe może również zastosować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców dla tych kontrolek i aplikacje klienckie nie trzeba podjąć specjalne kroki, aby uzyskać do nich dostęp.  
  
 Ten temat zawiera omówienie sposobu implementacji deweloperzy kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawców, szczególnie dla formantów w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] systemu windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy dostawców  
 Dostawcy automatyzacji interfejsu użytkownika można podzielić na dwie kategorie: dostawcy po stronie klienta i dostawcy po stronie serwera.  
  
### <a name="client-side-providers"></a>Dostawcy po stronie klienta  
 Dostawcy po stronie klienta są implementowane przez klientów automatyzacji interfejsu użytkownika do komunikowania się z aplikacji, która nie obsługuje lub nie obsługuje w pełni, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Dostawcy po stronie klienta zazwyczaj komunikacji z serwerem granicy procesu przez wysłanie i odebranie [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] wiadomości.  
  
 Ponieważ dostawców automatyzacji interfejsu użytkownika dla formantów w [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)], lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikacje są dostarczane jako część systemu operacyjnego, aplikacje klienckie rzadko zajść potrzeba wprowadzenia własnych dostawców i ten przegląd nie obejmują ich dodatkowych.  
  
### <a name="server-side-providers"></a>Dostawcy po stronie serwera  
 Dostawcy po stronie serwera są implementowane przez formanty niestandardowe lub aplikacje, które są oparte na framework interfejsu użytkownika innych niż [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)], lub [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostawcy po stronie serwera komunikacji z aplikacjami klienta granicy proces w przypadku wystawianego interfejsów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowe system, który z kolei obsługują żądania od klientów.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Pojęcia dotyczące dostawcy automatyzacji interfejsu użytkownika  
 Ta sekcja zawiera krótki wyjaśnienia dotyczące niektórych podstawowych pojęć, które należy poznać w celu wdrożenia dostawców automatyzacji interfejsu użytkownika.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są elementy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] widocznych dla klientów automatyzacji interfejsu użytkownika. Przykładami aplikacji systemu windows, okienka przycisków, etykietki narzędzi, pola listy i elementy listy.  
  
### <a name="navigation"></a>Nawigacji  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementy są widoczne dla klientów jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Tworzy drzewa przechodzenie z jednego elementu na inny. Nawigacja jest włączona przez dostawców dla każdego elementu, z których każdy może wskazywać elementu nadrzędnego, elementów równorzędnych i elementy podrzędne.  
  
 Aby uzyskać więcej informacji, w widoku klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Widoki  
 Klient może zobaczyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa w trzech głównych widoków, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Pierwotny widok|Zawiera wszystkie elementy.|  
|Kontrolki widoku|Zawiera elementy, które są formanty.|  
|Widok zawartości|Zawiera elementy, które mają zawartość.|  
  
 Aby uzyskać więcej informacji na temat widoków klienta programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Jest odpowiedzialny za implementacja dostawcy, aby zdefiniować element jako element zawartości lub element formantu. Elementy kontroli może lub nie można również elementów zawartości, ale wszystkie elementy zawartości są elementów formantu.  
  
### <a name="frameworks"></a>Struktury  
 Struktury jest składnikiem, który zarządza formantów podrzędnych, testowanie trafień i renderowanie w obszarze ekranu. Na przykład [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okna, często określany jako HWND może służyć jako platforma, która zawiera wiele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, takich jak paska menu, paska stanu i przycisków.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]Określa kontener, takich jak pola listy i widok drzewa są uważane za struktur, ponieważ zawierają one własny kod do renderowania elementów podrzędnych i wykonywania testowania trafień na nich. Z kolei [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pole listy nie jest platformy, ponieważ renderowania i testowanie trafień jest obsługiwane przez zawierający [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w aplikacji może składać się z różnych platform. Na przykład może zawierać okno aplikacji HWND [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] który z kolei zawiera składnik, takich jak pole kombi w HWND.  
  
### <a name="fragments"></a>fragmenty  
 Fragment jest pełne poddrzewo elementów z określonej struktury. Element w węźle głównym poddrzewa jest nazywany głównego fragmentu. Katalog główny fragmentu nie ma element nadrzędny, ale hostowanych w ramach innych systemu, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okna (HWND).  
  
### <a name="hosts"></a>Hosty  
 Węzeł główny każdego fragmentu musi być obsługiwana w elemencie zwykle [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okna (HWND). Wyjątek stanowi pulpitu, który nie znajduje się w innym elemencie. Host formant niestandardowy jest HWND samego formantu, nie okno aplikacji lub dowolnego innego okna, które mogą zawierać grup formantów najwyższego poziomu.  
  
 Host fragmentu odgrywa ważną rolę w dostarczaniu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usług. Umożliwia nawigacji do fragmentu głównego i udostępnia pewne domyślne właściwości tak, aby niestandardowego dostawcy nie trzeba ich wdrażania.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
