---
title: "Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 37110708efa49912d0ed9c81746d125167e17985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a>Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] można użyć do udostępnienia obiekty osadzone w zawartości kontrolki tekstu.  
  
> [!NOTE]
>  Osadzone obiekty mogą być obrazy, hiperłącza, przyciski, tabel lub kontrolki ActiveX.  
  
 Osadzone obiekty są traktowane jako elementy podrzędne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Umożliwia im to są dostępne za pośrednictwem taką samą strukturę drzewa automatyzacji interfejsu użytkownika, jak wszystkie inne [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów. Funkcje, jest z kolei za pośrednictwem wzorców formantu zwykle wymagane przez obiekty osadzone — typ formantu (na przykład, ponieważ hiperłączy tekstowych będzie obsługują <xref:System.Windows.Automation.TextPattern>).  
  
 ![Obiekty osadzone w kontenerze tekstu. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Przykładowy dokument z zawartości tekstowej, ("czy wiesz?" ...) dwa obiekty i osadzone (obraz wieloryb i hiperłącze tekstowe), używany jako obiekt docelowy dla przykładów kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób pobierania kolekcję osadzonych obiektów w programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. W dokumencie próbki w wprowadzenie dwa obiekty będzie zwracany (element obrazu i tekstowy element).  
  
> [!NOTE]
>  Element obrazu musi zawierać wewnętrzne tekst skojarzony z nim opisujący obrazu, zwykle w jego <xref:System.Windows.Automation.AutomationElement.NameProperty> (na przykład "niebieski wieloryb."). Jednak gdy są uzyskiwane spanning obiektu obrazu zakres tekstu, obrazu ani ten tekst opisu jest zwracany w strumieniu tekstu.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób uzyskiwania zakres tekstu z osadzonego obiektu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu. Zakres tekstu, pobierany jest pustego zakresu, w którym następuje początkowy punkt końcowy "... Oceanu. (miejsca) "i końcowy punkt końcowy poprzedza zamykającego". "reprezentujący osadzone hiperłącze (jak to przedstawiono obrazu dostarczonego w wprowadzenie). Nawet jeśli jest to pustego zakresu, nie uznaje się degeneracji zakresu ponieważ ma ona zakres inną niż zero.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern>można pobrać obiektu osadzonego tekstowych przykład hiperłącze; jednak dodatkowej <xref:System.Windows.Automation.TextPattern> musi pochodzić od obiektu osadzony Uwidacznianie pełną funkcjonalność.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
