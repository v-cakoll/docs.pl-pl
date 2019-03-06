---
title: 'Instrukcje: Usuń moduł definiowania układów z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 0c74fe9ed1e7190ce4ff26a7dbae1413f950ba7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374079"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Instrukcje: Usuń moduł definiowania układów z elementu
W tym przykładzie pokazano, jak programowo usunąć określonego modułu definiowania układu kodu z określonym <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu usuwa pierwszy moduł definiowania układu w tablica zwrócona przez moduły definiowania układu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  W tym przykładzie stanie się pobrać moduły definiowania układu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.  Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> ma nie definiowania `null` jest zwracana.  Ten kod jawnie sprawdza, czy tablicy o wartości null i jest najbardziej odpowiednia dla aplikacji, których powinien być stosunkowo wspólnej tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu skróconego jest funkcjonalnym odpowiednikiem pełny przykład pokazany powyżej. Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.  Ten kod jest najbardziej odpowiednie dla aplikacji, których oczekuje się rzadko tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Zobacz także
- [Moduły indeksowania układu — omówienie](adorners-overview.md)
