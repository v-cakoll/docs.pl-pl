---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a88822d6aed5af04ecf7deffe6936cfc4ebe296e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225953"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Produkty technologii pomocniczej i skrypty testowe Przejdź [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa w celu zbierania informacji o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jej elementów.  
  
 W ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest elementem głównym (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) reprezentujący obecnego pulpitu i którego elementy podrzędne reprezentują aplikacji systemu windows. Każda z tych elementów podrzędnych może zawierać elementów reprezentujących elementy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] takich jak menu, przyciski, paski narzędzi i pól listy. Z kolei te elementy mogą zawierać elementy, takie jak elementy listy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa nie jest stałą strukturę i rzadko jest widoczny w jego całość, ponieważ może on zawierać tysięcy elementów. Jej części są tworzone, ponieważ są one potrzebne, i może zostać poddane zmiany, jak elementy są dodawane, przeniesiony lub usunięty.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa przez zaimplementowanie Nawigacja między elementami w obrębie fragmentu, który składa się z elementem głównym (zwykle hostowane w oknie) i poddrzewa. Jednak dostawcy nie są związani z nawigacji z jednego formantu. To jest zarządzana przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowe, korzystając z informacji z domyślnych dostawców okna.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Widoki drzewa automatyzacji  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa można filtrować, aby utworzyć widoki, które zawierają tylko te <xref:System.Windows.Automation.AutomationElement> obiektów istotne dla konkretnego klienta. To podejście pozwala klientom dostosowywać struktury przedstawiane za pomocą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do ich potrzebom.  
  
 Klient ma dwa sposoby dostosowywania widoku: Określanie zakresu i filtrowania. Wyznaczanie zakresu jest zdefiniowanie zakresu widoku, zaczynając od elementu base: na przykład aplikacja może chcieć znaleźć tylko bezpośrednie elementy podrzędne pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie jest definiowanie typów elementów, które mają być uwzględniane w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują filtrowanie według Definiowanie właściwości elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> i <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> właściwości.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] udostępnia trzy domyślne widoki. Widoki te są definiowane przez typ filtrowania wykonywane; zakres dowolny widok jest zdefiniowany przez aplikację. Ponadto aplikację można stosować inne filtry właściwości; na przykład aby uwzględnić tylko włączone kontrolek w widoku formantu.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Nieprzetworzony widok  
 Nieprzetworzony widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo jest pełne drzewo <xref:System.Windows.Automation.AutomationElement> obiektów, dla których pulpitu jest obiektem głównym. Nieprzetworzony widok jest ściśle zgodna natywnych programowe struktury aplikacji i dlatego jest najbardziej szczegółowy widok dostępny. Jest również podstawowy, na którym są tworzone widoki drzewa. Ponieważ ten widok jest zależny od podstawowych [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, nieprzetworzony widok [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisk będzie miał inny widok pierwotne niż [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] przycisku.  
  
 Nieprzetworzony widok są uzyskiwane przez wyszukiwanie elementów bez określania właściwości lub za pomocą <xref:System.Windows.Automation.TreeWalker.RawViewWalker> Przejdź w drzewie.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Formant widoku  
 Widok kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa upraszcza zadanie produktów technologii pomocniczej opisujące [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikowi końcowemu i pomagając tego użytkownik końcowy wchodzić w interakcje z aplikacją, ponieważ jest on ściśle mapowany [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury postrzegane przez użytkownika końcowego.  
  
 Wyświetl formant jest podzbiorem nieprzetworzony widok. Zawiera wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów z surowy widok, który użytkownik końcowy może zrozumieć jako interaktywnego lub mającym swój wkład do struktury logicznej formantu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Przykłady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które przyczyniają się do Struktura logiczna [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nie są interaktywne samodzielnie, to kontenery elementów, takich jak nagłówki widoku listy, paski narzędzi, menu i paska stanu. Nieinterakcyjne elementy używane po prostu dla układu lub celów dekoracyjnych, nie będą widoczne w widoku kontrolnym. Przykładem jest panel, który został użyty tylko do tworzenia układu kontrolek w oknie dialogowym, ale sam nie zawiera żadnych informacji. Nieinterakcyjne elementy, które będą widoczne w widoku kontrolki są grafika z informacjami i tekst statyczny w oknie dialogowym. Nieinterakcyjne elementy, które znajdują się w widoku kontrolnym nie może odebrać fokus klawiatury.  
  
 Wyświetl formant uzyskuje się przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> właściwością `true`, lub za pomocą <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> Przejdź w drzewie.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Widok zawartości  
 Widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest podzbiorem widoku kontrolnym. Zawiera on [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które udzielają true informacji w interfejsie użytkownika, w tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które mogą odbierać klawiatury fokus i jakiś tekst, który nie jest etykietą na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Na przykład ponieważ stanowią one informacje używane przez użytkownika końcowego wartości w polu kombi listy rozwijanej pojawi się w widok zawartości. Widok zawartości pola kombi i pole listy są zarówno reprezentowane jako zbiór [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, w którym można wybrać jedną lub może być więcej niż jeden element. Fakt, że jeden jest zawsze otwarte i jedną można rozwijać i zwijać jest nie ma znaczenia w widoku zawartości, ponieważ jest przeznaczony do wyświetlania danych lub zawartości, która jest wyświetlenie użytkownikowi.  
  
 Widok zawartości są uzyskiwane przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> właściwością `true`, lub za pomocą <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> Przejdź w drzewie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement>
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
