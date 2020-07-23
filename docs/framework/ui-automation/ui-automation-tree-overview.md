---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
description: Przeczytaj przegląd dotyczący drzew automatyzacji interfejsu użytkownika. Dowiedz się więcej o różnych widokach drzewa automatyzacji interfejsu użytkownika, takich jak widok nieprzetworzony, widok formantów i widok zawartości.
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: 0ffe4b4e6157f5bff3284d6978e0ec28641cf72d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924555"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty technologii pomocniczej i Skrypty testowe przejdź [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do drzewa, aby zebrać informacje o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jego elementach.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie znajduje się element główny ( <xref:System.Windows.Automation.AutomationElement.RootElement%2A> ) reprezentujący bieżący pulpit, którego elementy podrzędne reprezentują okna aplikacji. Każdy z tych elementów podrzędnych może zawierać elementy reprezentujące fragmenty [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] takich jak menu, przyciski, paski narzędzi i pola listy. Te elementy z kolei mogą zawierać elementy, takie jak elementy listy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo nie jest stałą strukturą i rzadko jest widoczne w sumie, ponieważ może zawierać tysiące elementów. Części tego elementu są kompilowane w miarę ich konieczności i mogą być zmieniane, gdy elementy są dodawane, przenoszone lub usuwane.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo przez implementację nawigacji między elementami w obrębie fragmentu, która składa się z katalogu głównego (zazwyczaj hostowanego w oknie) i poddrzewa. Jednak dostawcy nie są zainteresowani nawigacją z jednej kontrolki do innej. Jest to zarządzane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rdzeń przy użyciu informacji z domyślnych dostawców okien.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Widoki drzewa automatyzacji  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Drzewo można filtrować w celu tworzenia widoków, które zawierają tylko te obiekty, które są <xref:System.Windows.Automation.AutomationElement> odpowiednie dla danego klienta. Takie podejście umożliwia klientom dostosowanie struktury przedstawionej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do konkretnych potrzeb.  
  
 Klient ma dwa sposoby dostosowywania widoku: przez określanie zakresu i filtrowanie. Określanie zakresu określa zakres widoku, rozpoczynając od elementu podstawowego: na przykład aplikacja może chcieć znaleźć tylko bezpośrednie elementy podrzędne pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie definiuje typy elementów, które mają być uwzględnione w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują filtrowanie przez Definiowanie właściwości elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> właściwości i.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zawiera trzy widoki domyślne. Te widoki są definiowane przez typ przeprowadzonego filtrowania; zakres każdego widoku jest definiowany przez aplikację. Ponadto aplikacja może stosować inne filtry na właściwościach; na przykład, aby uwzględnić tylko kontrolki włączone w widoku formantu.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Widok nieprzetworzony  
 Nieprzetworzony widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa to pełne drzewo <xref:System.Windows.Automation.AutomationElement> obiektów, dla których pulpit jest katalogiem głównym. Nieprzetworzony widok jest ściśle zgodny z natywną strukturą programistyczną aplikacji i dlatego jest najbardziej szczegółowym widokiem dostępnym. Jest to również podstawa, w której są kompilowane inne widoki drzewa. Ponieważ ten widok zależy od podstawowej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] platformy, widok nieprzetworzony [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisku będzie miał inny widok nieprzetworzony niż przycisk Win32.  
  
 Nieprzetworzony widok jest uzyskiwany przez wyszukiwanie elementów bez określania właściwości lub przy użyciu polecenia, <xref:System.Windows.Automation.TreeWalker.RawViewWalker> Aby nawigować do drzewa.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Widok kontrolki  
 Widok kontrolny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa upraszcza zadanie technologicznej technologii z opisem dla [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownika końcowego i pomaga użytkownikom końcowym korzystać z aplikacji, ponieważ dokładnie mapuje się do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury postrzeganej przez użytkownika końcowego.  
  
 Widok kontrolny jest podzbiorem widoku nieprzetworzonego. Zawiera wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy z widoku nieprzetworzonego, które użytkownik końcowy może zrozumieć jako interaktywny lub współtworzących strukturę logiczną formantu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Przykłady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które przyczyniają się do struktury logicznej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , ale nie są same interaktywnie, są kontenerami elementów, takimi jak nagłówki widoku listy, paski narzędzi, menu i pasek stanu. Nieinteraktywne elementy używane po prostu do układu lub dekoracyjnego nie będą widoczne w widoku sterowania. Przykładem jest panel, który był używany tylko do układania kontrolek w oknie dialogowym, ale sam nie zawiera żadnych informacji. Nieinteraktywne elementy, które będą widoczne w widoku kontrolki, to grafiki zawierające informacje i tekst statyczny w oknie dialogowym. Elementy nieinteraktywne, które znajdują się w widoku sterowania, nie mogą odbierać fokusu klawiatury.  
  
 Widok kontrolny jest uzyskiwany przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> Właściwość ustawioną na `true` lub przy użyciu polecenia, <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> Aby nawigować do drzewa.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Widok zawartości  
 Widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest podzbiorem widoku sterowania. Zawiera [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które są przekazujące prawdziwe informacje w interfejsie użytkownika, w tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które mogą odbierać fokus klawiatury, a także tekst, który nie jest etykietą [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Na przykład wartości w polu kombi listy rozwijanej będą wyświetlane w widoku zawartości, ponieważ reprezentują informacje używane przez użytkownika końcowego. W widoku zawartości pole kombi i pole listy są reprezentowane jako kolekcja [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, w których można wybrać jedną lub więcej niż jeden element. Oznacza to, że jeden jest zawsze otwarty i jeden z nich może rozwijać i zwijać nie jest istotny w widoku zawartości, ponieważ został zaprojektowany, aby pokazać dane lub zawartość, która jest prezentowana użytkownikowi.  
  
 Widok zawartości jest uzyskiwany przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> Właściwość ustawioną na `true` lub przy użyciu polecenia, <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> Aby nawigować do drzewa.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement>
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
