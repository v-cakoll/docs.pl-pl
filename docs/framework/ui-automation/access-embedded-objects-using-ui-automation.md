---
title: Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 83e54da5fdb75e3da44009ec700102d6bd7ae5e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937963"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie pokazano [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , jak można użyć programu w celu uwidocznienia obiektów osadzonych w zawartości kontrolki tekstu.  
  
> [!NOTE]
> Obiekty osadzone mogą zawierać obrazy, hiperłącza, przyciski, tabele lub kontrolki ActiveX.  
  
 Obiekty osadzone są uważane za elementy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podrzędne dostawcy tekstu. Pozwala to na uwidocznienie ich za pomocą tej samej struktury drzewa automatyzacji interfejsu użytkownika co [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] wszystkie inne elementy. Z kolei funkcje są udostępniane za pośrednictwem wzorców formantów zwykle wymaganych przez typ formantu osadzone obiekty (na przykład, ponieważ hiperłącza są obsługiwane <xref:System.Windows.Automation.TextPattern>na podstawie tekstu).  
  
 ![Obiekty osadzone w kontenerze tekstu.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Przykładowy dokument z zawartością tekstową ("Czy wiesz?" ...) i dwa osadzone obiekty (obraz Whale i Hiperłącze tekstowe) używane jako element docelowy dla przykładów kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób pobierania kolekcji obiektów osadzonych z poziomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. W przypadku przykładowego dokumentu dostarczonego we wprowadzeniu zostaną zwrócone dwa obiekty (element obrazu i element tekstowy).  
  
> [!NOTE]
> Do elementu obrazu powinien być skojarzony jakiś wewnętrzny tekst, który zawiera opis obrazu, zazwyczaj w jego <xref:System.Windows.Automation.AutomationElement.NameProperty> (na przykład "niebieska Whale."). Jednak gdy zostanie uzyskany zakres tekstu obejmujący obiekt obrazu, w strumieniu tekstowym nie jest zwracany ani obraz, ani ten tekst opisujący.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak uzyskać zakres tekstu z osadzonego obiektu w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Pobrany zakres tekstu jest pustym zakresem, w którym znajduje się początkowy punkt końcowy "... utworzeniu. (Space) ", a końcowy koniec poprzedza nawias". "reprezentujący osadzone hiperłącze (jak pokazano w obrazie podanym we wprowadzeniu). Mimo że jest to pusty zakres, nie jest uważany za wygenerowanego zakresu, ponieważ jego zakres jest różny od zera.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern>może pobrać obiekt osadzony tekstowy, taki jak hiperlink; jednak pomocniczy <xref:System.Windows.Automation.TextPattern> należy uzyskać z osadzonego obiektu, aby uwidocznić jego pełną funkcjonalność.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
