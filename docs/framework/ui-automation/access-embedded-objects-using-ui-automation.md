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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 05f9359aa055019b517abb1b7c86ca386d630e41
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513973"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] może służyć do udostępnienia obiektów osadzonych w zawartości kontrolki tekstu.  
  
> [!NOTE]
>  Może zawierać obiekty osadzone, obrazy, hiperłącza, przyciski, tabel lub kontrolki ActiveX.  
  
 Osadzone obiekty są traktowane jako elementy podrzędne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Dzięki temu można uwidocznić za pośrednictwem tej samej struktury drzewa automatyzacji interfejsu użytkownika, jak wszystkie inne [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów. Funkcje, z kolei jest dostępna za pośrednictwem wzorców kontrolek, zwykle wymagane przez obiekty osadzone typu formantu (na przykład, ponieważ hiperłącza są oparte na tekście zostanie obsługują <xref:System.Windows.Automation.TextPattern>).  
  
 ![Obiekty osadzone w kontenerze tekstu. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Przykładowy dokument z zawartości tekstowej ("czy wiesz?" ...) dwa obiekty i osadzone (obraz whale i hiperłącze tekstowe), używany jako obiekt docelowy dla przykładów kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak pobrać kolekcję obiektów osadzonych z poziomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Dla dokumentu próbki, podane we wstępie dwa obiekty będzie zwracany (element obrazu i element tekstowy).  
  
> [!NOTE]
>  Element obrazu musi zawierać część wewnętrzne tekstu skojarzonych z nim, opisujący obrazu, zazwyczaj w jego <xref:System.Windows.Automation.AutomationElement.NameProperty> (na przykład "niebieski whale."). Jednak po uzyskaniu zakres tekstu, obejmujące obiekt obrazu obrazu ani ten tekst opisu jest zwracany w strumieniu tekstu.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób uzyskiwania zakres tekstu z obiektu osadzonego w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Zakres tekstu, pobierane jest pustego zakresu, gdzie następuje początkowy punkt końcowy "... Ocean. (miejsca) "i końcowej punktu końcowego poprzedza zamknięcia". "reprezentujący osadzone hiperłącze (jak to przedstawiono obrazu dostarczonego we wstępie). Nawet jeśli jest to pustego zakresu, nie uważa się zakres wymiaru degeneracji ponieważ ma zakres od zera.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> można pobrać oparte na tekście osadzony obiekt na przykład hiperłącze. jednak pomocniczy <xref:System.Windows.Automation.TextPattern> musi pochodzić z osadzonego obiektu do udostępnienia pełną funkcjonalność.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
