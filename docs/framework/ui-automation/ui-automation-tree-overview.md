---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: f541aab7ed5aae48b943ba5699366fe6a3f21a4c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741391"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty technologii pomocniczej i Skrypty testowe przejdź do drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aby zebrać informacje o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jego elementach.  
  
 W drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istnieje element główny (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) reprezentujący bieżący pulpit, którego elementy podrzędne reprezentują okna aplikacji. Każdy z tych elementów podrzędnych może zawierać elementy reprezentujące fragmenty [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], takie jak menu, przyciski, paski narzędzi i pola listy. Te elementy z kolei mogą zawierać elementy, takie jak elementy listy.  
  
 Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie jest stałą strukturą i rzadko jest widoczne w sumie, ponieważ może zawierać tysiące elementów. Części tego elementu są kompilowane w miarę ich konieczności i mogą być zmieniane, gdy elementy są dodawane, przenoszone lub usuwane.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez implementację nawigacji między elementami w obrębie fragmentu, która składa się z katalogu głównego (zazwyczaj hostowanego w oknie) i poddrzewa. Jednak dostawcy nie są zainteresowani nawigacją z jednej kontrolki do innej. Jest to zarządzane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rdzeń przy użyciu informacji z domyślnych dostawców okien.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Widoki drzewa automatyzacji  
 Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można filtrować w celu tworzenia widoków, które zawierają tylko te obiekty <xref:System.Windows.Automation.AutomationElement> odpowiednie dla danego klienta. Takie podejście umożliwia klientom dostosowanie struktury przedstawionej w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do ich konkretnych potrzeb.  
  
 Klient ma dwa sposoby dostosowywania widoku: przez określanie zakresu i filtrowanie. Określanie zakresu określa zakres widoku, rozpoczynając od elementu podstawowego: na przykład aplikacja może chcieć znaleźć tylko bezpośrednie elementy podrzędne pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie definiuje typy elementów, które mają być uwzględnione w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują filtrowanie przez Definiowanie właściwości dla elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> i <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> właściwości.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] udostępnia trzy widoki domyślne. Te widoki są definiowane przez typ przeprowadzonego filtrowania; zakres każdego widoku jest definiowany przez aplikację. Ponadto aplikacja może stosować inne filtry na właściwościach; na przykład, aby uwzględnić tylko kontrolki włączone w widoku formantu.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Widok nieprzetworzony  
 Nieprzetworzony widok drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest pełnym drzewem obiektów <xref:System.Windows.Automation.AutomationElement>, dla których pulpit jest katalogiem głównym. Nieprzetworzony widok jest ściśle zgodny z natywną strukturą programistyczną aplikacji i dlatego jest najbardziej szczegółowym widokiem dostępnym. Jest to również podstawa, w której są kompilowane inne widoki drzewa. Ponieważ ten widok zależy od bazowej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Framework, nieprzetworzony widok przycisku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] będzie miał inny widok pierwotny niż przycisk Win32.  
  
 Nieprzetworzony widok jest uzyskiwany przez wyszukiwanie elementów bez określania właściwości lub przy użyciu <xref:System.Windows.Automation.TreeWalker.RawViewWalker> do nawigowania po drzewie.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Widok kontrolki  
 Widok kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] upraszcza zadanie dotyczące technologii wspomagającej opisywanie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikowi końcowemu i pomagając użytkownikowi końcowemu korzystać z aplikacji, ponieważ dokładnie mapuje się do struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] postrzeganej przez użytkownika końcowego.  
  
 Widok kontrolny jest podzbiorem widoku nieprzetworzonego. Zawiera wszystkie elementy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z widoku nieprzetworzonego, który użytkownik końcowy może zrozumieć jako interaktywny lub współautorem struktury logicznej kontrolki w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Przykłady elementów [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], które przyczyniają się do struktury logicznej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nie są same interaktywnie, są kontenerami elementów, takimi jak nagłówki widoku listy, paski narzędzi, menu i pasek stanu. Nieinteraktywne elementy używane po prostu do układu lub dekoracyjnego nie będą widoczne w widoku sterowania. Przykładem jest panel, który był używany tylko do układania kontrolek w oknie dialogowym, ale sam nie zawiera żadnych informacji. Nieinteraktywne elementy, które będą widoczne w widoku kontrolki, to grafiki zawierające informacje i tekst statyczny w oknie dialogowym. Elementy nieinteraktywne, które znajdują się w widoku sterowania, nie mogą odbierać fokusu klawiatury.  
  
 Widok kontrolny jest uzyskiwany przez wyszukiwanie elementów mających Właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> ustawione na `true`lub przy użyciu <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> do nawigowania po drzewie.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Widok zawartości  
 Widok zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest podzbiorem widoku sterowania. Zawiera [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które są przekazujące prawdziwe informacje w interfejsie użytkownika, w tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które mogą odbierać fokus klawiatury i część tekstu, który nie jest etykietą elementu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Na przykład wartości w polu kombi listy rozwijanej będą wyświetlane w widoku zawartości, ponieważ reprezentują informacje używane przez użytkownika końcowego. W widoku zawartości pole kombi i pole listy są reprezentowane jako kolekcja elementów [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], w których można wybrać jedną lub więcej niż jeden element. Oznacza to, że jeden jest zawsze otwarty i jeden z nich może rozwijać i zwijać nie jest istotny w widoku zawartości, ponieważ został zaprojektowany, aby pokazać dane lub zawartość, która jest prezentowana użytkownikowi.  
  
 Widok zawartości jest uzyskiwany przez wyszukiwanie elementów mających Właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> ustawione na `true`lub przy użyciu <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> do nawigowania po drzewie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement>
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
