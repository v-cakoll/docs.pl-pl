---
title: 'Instrukcje: Usuwanie wszystkich modułów definiowania układów z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116797"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>Instrukcje: Usuwanie wszystkich modułów definiowania układów z elementu
W tym przykładzie pokazano, jak programowo usunąć wszystkie moduły definiowania układów z określonym <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu usuwa wszystkie moduły definiowania układu w tablica zwrócona przez moduły definiowania układu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  W tym przykładzie stanie się pobrać moduły definiowania układu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.  Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> ma nie definiowania `null` jest zwracana.  Ten kod jawnie sprawdza, czy tablicy o wartości null i jest najbardziej odpowiednia dla aplikacji, których powinien być stosunkowo wspólnej tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu skróconego jest funkcjonalnym odpowiednikiem pełny przykład pokazany powyżej. Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.  Ten kod jest najbardziej odpowiednie dla aplikacji, których oczekuje się rzadko tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Moduły indeksowania układu](adorners-overview.md)
