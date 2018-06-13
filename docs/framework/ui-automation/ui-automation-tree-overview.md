---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0823a569b19d46f32c1cb780470a935f20429c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409126"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Produkty technologii pomocniczej i skryptów testu Przejdź [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa do zbierania informacji o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jej elementów.  
  
 W ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest elementem głównym (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) reprezentujący bieżącego pulpitu i którego elementy podrzędne reprezentują aplikacji systemu windows. Każdy z tych elementów podrzędnych może zawierać elementy reprezentujące części [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] np. menu, paski narzędzi, przycisków i pola listy. Z kolei te elementy mogą zawierać elementów, takich jak elementy listy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa nie jest stałą strukturę i rzadko jest widoczna w jego całość, ponieważ może ona zawierać tysięcy elementów. Części są tworzone są potrzebne, i może zostać poddane zmiany, jak dodać, przenieść lub usunąć elementy.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa zaimplementowanie nawigacji między elementów w obrębie fragmentu, która składa się z głównym (zazwyczaj obsługiwanych w oknie) i poddrzewo. Jednak dostawców nie są związane z nawigacji z jednego formantu. Jest ona zarządzana przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowe, korzystając z informacji z domyślnych dostawców okna.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Widoki Automatyzacja drzewa  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa mogą być filtrowane do tworzenia widoków, które zawierają tylko te <xref:System.Windows.Automation.AutomationElement> obiektów istotne dla określonego klienta. Takie podejście umożliwia klientom dostosować struktury przedstawiane w programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do ich potrzebom.  
  
 Klient ma dwa sposoby dostosowywania widoku: Określanie zakresu i filtrowania. Zakres jest zdefiniowanie zakresu widoku, zaczynając od base element: na przykład aplikacja może być znalezienie tylko bezpośrednimi elementami podrzędnymi pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie jest definiowanie typów elementów, które mają być uwzględniane w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługuje filtrowanie, definiując właściwości dla elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> i <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> właściwości.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] udostępnia trzy widoki. Widoki te są definiowane przez typ filtrowania wykonywane; zakres dowolnego widoku jest zdefiniowany przez aplikację. Ponadto aplikacji można stosować inne filtry właściwości; na przykład aby uwzględnić tylko włączone formantów w widoku kontrolki.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Pierwotny widok  
 Nieprzetworzona widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo jest pełna drzewa <xref:System.Windows.Automation.AutomationElement> obiektów, dla których pulpitu jest elementem głównym. Pierwotny widok jest ściśle zgodna natywnego programowe struktury aplikacji i dlatego jest najbardziej szczegółowy widok dostępny. Możliwe jest również podstawowy, na którym są wbudowane widoki drzewa. Ponieważ ten widok jest zależny od odpowiadającego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, widok raw [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisk będzie mieć inny widok raw niż [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] przycisku.  
  
 Pierwotny widok są uzyskiwane przez wyszukiwanie elementów bez określania właściwości lub za pomocą <xref:System.Windows.Automation.TreeWalker.RawViewWalker> do przechodzenia drzewa.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Kontrolki widoku  
 Formant widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa upraszcza opisu produktów technologii pomocniczej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikowi końcowemu i pomoc tego użytkownika końcowego interakcji z aplikacją ponieważ ściśle mapowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] — struktura postrzegane przez użytkownika końcowego.  
  
 W widoku kontrolki jest podzbiorem pierwotnego widoku. Zawiera wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy z pierwotnego widoku, który użytkownik końcowy będzie jako interaktywnego lub uczestniczący w strukturze logicznej formantu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Przykłady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które przyczyniają się do struktury logicznej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nie są interakcyjne siebie, są kontenerami elementów, takich jak nagłówki widoku listy, paski narzędzi, menu i paska stanu. Elementy nieinterakcyjne używany po prostu do celów ozdobne lub układ nie będą widoczne w widoku kontrolki. Przykładem jest panelu, które zostało użyte tylko do tworzenia układu kontrolek w oknie dialogowym, ale sam nie zawiera żadnych informacji. Nieinterakcyjne elementy, które będą widoczne w widoku kontrolki są informacje i statyczny tekst w oknie dialogowym. Nieinterakcyjne elementy, które znajdują się w widoku kontrolki nie można ustawić fokusu klawiatury.  
  
 W widoku kontrolki są uzyskiwane przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> ustawioną właściwość `true`, lub za pomocą <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> do przechodzenia drzewa.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Widok zawartości  
 Widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest podzbiorem formantu widoku. Zawiera on [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które udzielają true informacji w interfejsie użytkownika, w tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które mogą odbierać klawiatura fokus i tekst, który nie jest etykietą na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Na przykład wartości w polu kombi listy rozwijanej będą wyświetlane w widoku zawartości, ponieważ stanowią one informacje używane przez użytkownika końcowego. W widoku zawartości pole kombi i pole listy są oba reprezentowane jako kolekcja [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, w którym można wybrać co najmniej prawdopodobnie więcej niż jeden element. Fakt, że jeden zawsze jest otwarty i co można zwijać i rozwijać jest istotny w widoku zawartości, ponieważ jest przeznaczony do wyświetlania danych lub zawartości, która jest zgłoszenia do użytkownika.  
  
 Widok zawartości są uzyskiwane przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> ustawioną właściwość `true`, lub za pomocą <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> do przechodzenia drzewa.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.AutomationElement>  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
