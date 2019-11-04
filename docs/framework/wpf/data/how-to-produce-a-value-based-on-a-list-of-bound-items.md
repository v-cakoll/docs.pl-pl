---
title: Jak uzyskać wartość w oparciu o listę powiązanych elementów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459696"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Jak uzyskać wartość w oparciu o listę powiązanych elementów
<xref:System.Windows.Data.MultiBinding> umożliwia powiązanie właściwości celu powiązania z listą właściwości źródła, a następnie zastosowanie logiki w celu utworzenia wartości z danymi wejściowymi. W tym przykładzie pokazano, jak używać <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `NameListData` odnosi się do kolekcji obiektów `PersonName`, które są obiektami zawierającymi dwie właściwości, `firstName` i `lastName`. Poniższy przykład generuje <xref:System.Windows.Controls.TextBlock>, który najpierw wyświetla imię i nazwisko osoby o nazwisku nazwisko.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Aby zrozumieć, w jaki sposób jest tworzony format last-name-First, przyjrzyjmy się implementacji `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implementuje interfejs <xref:System.Windows.Data.IMultiValueConverter>. `NameConverter` pobiera wartości z poszczególnych powiązań i zapisuje je w tablicy obiektów wartości. Kolejność, w której elementy <xref:System.Windows.Data.Binding> są wyświetlane pod elementem <xref:System.Windows.Data.MultiBinding>, jest kolejnością, w której te wartości są przechowywane w tablicy. Wartość atrybutu <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> jest przywoływana przez argument Parameter metody <xref:System.Windows.Data.MultiBinding.Converter%2A>, która wykonuje przełącznik na parametrze, aby określić sposób formatowania nazwy.  
  
## <a name="see-also"></a>Zobacz także

- [Konwertowanie powiązanych danych](how-to-convert-bound-data.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
