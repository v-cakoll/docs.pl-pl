---
title: 'Instrukcje: Tworzenie prostego powiązania'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931572"
---
# <a name="how-to-create-a-simple-binding"></a>Instrukcje: Tworzenie prostego powiązania
W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`. `Person` Obiekt jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.  
  
 Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`. Jest to realizowane w `Resources` sekcji i przypisane `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> kontrolę `PersonName` właściwości. W rezultacie <xref:System.Windows.Controls.TextBlock> pojawi się wartość "Jan".  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
