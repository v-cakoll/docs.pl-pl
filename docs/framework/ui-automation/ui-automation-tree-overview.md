---
title: Przegląd drzewa automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a0b888e8ecc80e3739c583931a86da3cdb7242d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179455"
---
# <a name="ui-automation-tree-overview"></a>Przegląd drzewa automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty technologii pomocniczej i skrypty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] testowe nawigują po drzewie w celu zebrania [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] informacji o elementach i jego elementach.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie znajduje się<xref:System.Windows.Automation.AutomationElement.RootElement%2A>element główny ( ), który reprezentuje bieżący pulpit i którego elementy podrzędne reprezentują okna aplikacji. Każdy z tych elementów podrzędnych może [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zawierać elementy reprezentujące elementy, takie jak menu, przyciski, paski narzędzi i pola listy. Te elementy z kolei mogą zawierać elementy, takie jak elementy listy.  
  
 Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie jest stałą strukturą i rzadko jest widoczne w całości, ponieważ może zawierać tysiące elementów. Jego części są budowane w miarę ich potrzeb i mogą ulegać zmianom w miarę dodawania, przenoszenia lub usuwania elementów.  
  
 Dostawcy automatyzacji interfejsu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] użytkownika obsługują drzewa, implementując nawigację między elementami we fragmencie, który składa się z katalogu głównego (zwykle hostowanego w oknie) i poddrzewa. Dostawcy nie zajmują się jednak nawigacją z jednego formantu do drugiego. Jest to zarządzane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przez rdzeń, przy użyciu informacji od domyślnych dostawców okien.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Widoki drzewa automatyzacji  
 Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można filtrować, aby utworzyć widoki, które zawierają tylko te <xref:System.Windows.Automation.AutomationElement> obiekty istotne dla określonego klienta. Takie podejście pozwala klientom dostosować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę przedstawioną do ich szczególnych potrzeb.  
  
 Klient ma dwa sposoby dostosowywania widoku: przez zakres i filtrowanie. Zakres jest definiowanie zakresu widoku, począwszy od elementu podstawowego: na przykład aplikacja może chcieć znaleźć tylko bezpośrednie elementy podrzędne pulpitu lub wszystkie elementy podrzędne okna aplikacji. Filtrowanie definiuje typy elementów, które mają być uwzględnione w widoku.  
  
 Dostawcy automatyzacji interfejsu użytkownika obsługują filtrowanie, definiując właściwości elementów, w tym <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> właściwości i. <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia trzy widoki domyślne. Widoki te są definiowane przez typ wykonywanego filtrowania; zakres każdego widoku jest zdefiniowany przez aplikację. Ponadto aplikacja może zastosować inne filtry na właściwości; na przykład, aby uwzględnić tylko włączone formanty w widoku sterowania.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Widok nieprzetworzony  
 Nieprzetworzony [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widok drzewa jest <xref:System.Windows.Automation.AutomationElement> pełnym drzewem obiektów, dla których pulpit jest katalogiem głównym. Widok nieprzetworzony ściśle jest zgodny z natywną strukturą programową aplikacji i dlatego jest najbardziej szczegółowym dostępnym widokiem. Jest to również podstawa, na której zbudowane są inne widoki drzewa. Ponieważ ten widok zależy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] od podstawowej struktury, nieprzetworzony [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] widok przycisku będzie miał inny widok pierwotny niż przycisk Win32.  
  
 Widok nieprzetworzony uzyskuje się przez wyszukiwanie elementów <xref:System.Windows.Automation.TreeWalker.RawViewWalker> bez określania właściwości lub za pomocą do nawigacji drzewa.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Widok sterowania  
 Widok kontrolny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa upraszcza zadanie produktu technologii pomocniczej opisujące [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownika końcowego i pomoc temu użytkownikowi końcowemu w interakcji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z aplikacją, ponieważ ściśle mapuje strukturę postrzeganą przez użytkownika końcowego.  
  
 Widok kontrolny jest podzbiorem widoku nieprzetworzonego. Zawiera wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy z widoku nieprzetworzonego, które użytkownik końcowy zrozumiałby jako [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]interaktywne lub przyczyniające się do logicznej struktury formantu w pliku . Przykładami [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, które przyczyniają się [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]do struktury logicznej , ale nie są interaktywne, są kontenery elementów, takich jak nagłówki widoku listy, paski narzędzi, menu i pasek stanu. Elementy nieinteraktywne używane po prostu do celów układu lub dekoracyjnych nie będą widoczne w widoku kontrolnym. Przykładem jest panel, który był używany tylko do rozmieść formanty w oknie dialogowym, ale sam nie zawiera żadnych informacji. Elementy nieinterakcyjne, które będą widoczne w widoku formantu, to grafika z informacjami i tekstem statycznym w oknie dialogowym. Elementy nieinterakcyjne, które są zawarte w widoku sterowania, nie mogą odbierać fokusu klawiatury.  
  
 Widok formantu uzyskuje się przez <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> wyszukiwanie elementów, które <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> mają właściwość ustawioną na `true`, lub za pomocą do nawigacji drzewa.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Widok zawartości  
 Widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa jest podzbiorem widoku formantu. Zawiera [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, które przekazują prawdziwe informacje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w interfejsie użytkownika, w tym elementy, które [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mogą odbierać fokus klawiatury i niektóre tekst, który nie jest etykietą na elemencie. Na przykład wartości w polu kombi rozwijanej pojawią się w widoku zawartości, ponieważ reprezentują informacje używane przez użytkownika końcowego. W widoku zawartości pole kombi i pole listy są reprezentowane jako kolekcja [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, w których można wybrać jeden lub być może więcej niż jeden element. Fakt, że jeden jest zawsze otwarty i można rozwinąć i zwinąć, nie ma znaczenia w widoku zawartości, ponieważ jest przeznaczony do wyświetlania danych lub zawartości, które są prezentowane użytkownikowi.  
  
 Widok zawartości uzyskuje się przez wyszukiwanie <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> elementów, `true`które mają <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> właściwość ustawioną na , lub za pomocą do nawigacji drzewa.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.AutomationElement>
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
