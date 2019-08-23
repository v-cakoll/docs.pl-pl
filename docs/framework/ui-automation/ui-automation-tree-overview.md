---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: 7dd799b32d51c7e24e6717561aab549e7e7f1fbe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954007"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Produkty technologii pomocniczej i Skrypty testowe przejdź [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do drzewa, aby zebrać informacje [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] o i jego elementach.  
  
 W drzewie znajduje się element główny (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) reprezentujący bieżący pulpit, którego elementy podrzędne reprezentują okna aplikacji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Każdy z tych elementów podrzędnych może zawierać elementy reprezentujące fragmenty [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] takich jak menu, przyciski, paski narzędzi i pola listy. Te elementy z kolei mogą zawierać elementy, takie jak elementy listy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo nie jest stałą strukturą i rzadko jest widoczne w sumie, ponieważ może zawierać tysiące elementów. Części tego elementu są kompilowane w miarę ich konieczności i mogą być zmieniane, gdy elementy są dodawane, przenoszone lub usuwane.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo przez implementację nawigacji między elementami w obrębie fragmentu, która składa się z katalogu głównego (zazwyczaj hostowanego w oknie) i poddrzewa. Jednak dostawcy nie są zainteresowani nawigacją z jednej kontrolki do innej. Jest to zarządzane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rdzeń przy użyciu informacji z domyślnych dostawców okien.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Widoki drzewa automatyzacji  
 Drzewo można filtrować w celu tworzenia widoków, które zawierają tylko te <xref:System.Windows.Automation.AutomationElement> obiekty, które są odpowiednie dla danego klienta. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Takie podejście umożliwia klientom dostosowanie struktury przedstawionej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do konkretnych potrzeb.  
  
 Klient ma dwa sposoby dostosowywania widoku: przez określanie zakresu i filtrowanie. Określanie zakresu określa zakres widoku, rozpoczynając od elementu podstawowego: na przykład aplikacja może chcieć znaleźć tylko bezpośrednie elementy podrzędne pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie definiuje typy elementów, które mają być uwzględnione w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują filtrowanie przez Definiowanie właściwości elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> właściwości <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> i.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zawiera trzy widoki domyślne. Te widoki są definiowane przez typ przeprowadzonego filtrowania; zakres każdego widoku jest definiowany przez aplikację. Ponadto aplikacja może stosować inne filtry na właściwościach; na przykład, aby uwzględnić tylko kontrolki włączone w widoku formantu.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Widok nieprzetworzony  
 Nieprzetworzony widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa to pełne <xref:System.Windows.Automation.AutomationElement> drzewo obiektów, dla których pulpit jest katalogiem głównym. Nieprzetworzony widok jest ściśle zgodny z natywną strukturą programistyczną aplikacji i dlatego jest najbardziej szczegółowym widokiem dostępnym. Jest to również podstawa, w której są kompilowane inne widoki drzewa. Ponieważ ten widok zależy od podstawowej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktury, pierwotny widok [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisku będzie miał [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] inny nieprzetworzony widok niż przycisk.  
  
 Nieprzetworzony widok jest uzyskiwany przez wyszukiwanie elementów bez określania właściwości lub przy użyciu polecenia <xref:System.Windows.Automation.TreeWalker.RawViewWalker> , aby nawigować do drzewa.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Widok kontrolki  
 Widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolny drzewa upraszcza zadanie technologicznej technologii z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] opisem dla użytkownika końcowego i pomaga użytkownikom końcowym korzystać z aplikacji, ponieważ dokładnie mapuje się na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] strukturę postrzegane przez użytkownika końcowego.  
  
 Widok kontrolny jest podzbiorem widoku nieprzetworzonego. Zawiera wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy z widoku nieprzetworzonego, które użytkownik końcowy może zrozumieć jako interaktywny lub współtworzących strukturę logiczną formantu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]w. Przykłady elementów, które przyczyniają się do struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]logicznej, ale nie są same interaktywnie, są kontenerami elementów, takimi jak nagłówki widoku listy, paski narzędzi, menu i pasek stanu. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Nieinteraktywne elementy używane po prostu do układu lub dekoracyjnego nie będą widoczne w widoku sterowania. Przykładem jest panel, który był używany tylko do układania kontrolek w oknie dialogowym, ale sam nie zawiera żadnych informacji. Nieinteraktywne elementy, które będą widoczne w widoku kontrolki, to grafiki zawierające informacje i tekst statyczny w oknie dialogowym. Elementy nieinteraktywne, które znajdują się w widoku sterowania, nie mogą odbierać fokusu klawiatury.  
  
 Widok kontrolny jest uzyskiwany przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> Właściwość ustawioną `true`na lub przy użyciu polecenia <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> , aby nawigować do drzewa.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Widok zawartości  
 Widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa jest podzbiorem widoku sterowania. Zawiera [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które są przekazujące prawdziwe informacje w interfejsie użytkownika, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w tym elementy, które mogą odbierać fokus klawiatury, a także tekst, który [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nie jest etykietą elementu. Na przykład wartości w polu kombi listy rozwijanej będą wyświetlane w widoku zawartości, ponieważ reprezentują informacje używane przez użytkownika końcowego. W widoku zawartości pole kombi i pole listy są reprezentowane jako kolekcja [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, w których można wybrać jedną lub więcej niż jeden element. Oznacza to, że jeden jest zawsze otwarty i jeden z nich może rozwijać i zwijać nie jest istotny w widoku zawartości, ponieważ został zaprojektowany, aby pokazać dane lub zawartość, która jest prezentowana użytkownikowi.  
  
 Widok zawartości jest uzyskiwany przez wyszukiwanie elementów, które mają <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> Właściwość ustawioną na `true`lub przy użyciu polecenia <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> , aby nawigować do drzewa.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement>
- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
