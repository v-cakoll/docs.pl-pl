---
title: Jak użyć słownika zasobów zakresu aplikacji
description: Dowiedz się, jak definiować i używać niestandardowego słownika zasobów zakresu aplikacji w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613712"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Jak użyć słownika zasobów zakresu aplikacji
Ten przykład przedstawia sposób definiowania i używania niestandardowego słownika zasobów zakresu aplikacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Application>uwidacznia magazyn zakresu aplikacji dla zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A> . Domyślnie <xref:System.Windows.Application.Resources%2A> Właściwość jest inicjowana przy użyciu wystąpienia <xref:System.Windows.ResourceDictionary> typu. To wystąpienie jest używane podczas pobierania i ustawiania właściwości zakresu aplikacji przy użyciu <xref:System.Windows.Application.Resources%2A> . Aby uzyskać więcej informacji, zobacz [jak: pobieranie i Ustawianie zasobu zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Jeśli masz wiele zasobów ustawionych przy użyciu programu <xref:System.Windows.Application.Resources%2A> , możesz zamiast tego użyć niestandardowego słownika zasobów do przechowywania tych zasobów i ustawić <xref:System.Windows.Application.Resources%2A> je w zamian. Poniżej przedstawiono sposób deklarowania niestandardowego słownika zasobów przy użyciu języka XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Wymiana całych słowników zasobów przy użyciu programu <xref:System.Windows.Application.Resources%2A> umożliwia obsługę motywów zakresu aplikacji, gdzie każdy motyw jest hermetyzowany przez pojedynczy słownik zasobów. Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary> .  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Poniżej przedstawiono sposób pobierania zasobów zakresu aplikacji z słownika zasobów uwidocznionych <xref:System.Windows.Application.Resources%2A> w języku XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Poniżej pokazano, jak można także uzyskać zasoby w kodzie.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Istnieją dwa kwestie, które należy wziąć pod uwagę podczas korzystania z programu <xref:System.Windows.Application.Resources%2A> . Najpierw *klucz* słownika jest obiektem, dlatego należy użyć dokładnie tego samego wystąpienia obiektu, gdy oba ustawienia i pobierają wartość właściwości. (Należy pamiętać, że podczas korzystania z ciągu w kluczu jest rozróżniana wielkość liter). Po drugie, *wartość* słownika jest obiektem, dlatego konieczne będzie przekonwertowanie wartości na żądany typ podczas pobierania wartości właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Połączone słowniki zasobów](../advanced/merged-resource-dictionaries.md)
