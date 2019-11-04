---
title: Jak użyć słownika zasobów zakresu aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459797"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Jak użyć słownika zasobów zakresu aplikacji
Ten przykład przedstawia sposób definiowania i używania niestandardowego słownika zasobów zakresu aplikacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Application> uwidacznia magazyn zakresu aplikacji dla zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A>. Domyślnie właściwość <xref:System.Windows.Application.Resources%2A> jest inicjowana przy użyciu wystąpienia typu <xref:System.Windows.ResourceDictionary>. To wystąpienie jest używane podczas pobierania i ustawiania właściwości zakresu aplikacji przy użyciu <xref:System.Windows.Application.Resources%2A>. Aby uzyskać więcej informacji, zobacz [jak: pobieranie i Ustawianie zasobu zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Jeśli masz wiele zasobów ustawionych przy użyciu <xref:System.Windows.Application.Resources%2A>, zamiast tego możesz użyć niestandardowego słownika zasobów do przechowywania tych zasobów i ustawić w zamian <xref:System.Windows.Application.Resources%2A>. Poniżej przedstawiono sposób deklarowania niestandardowego słownika zasobów przy użyciu języka XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Wymiana całych słowników zasobów przy użyciu <xref:System.Windows.Application.Resources%2A> umożliwia obsługę motywów zakresu aplikacji, gdzie każdy motyw jest hermetyzowany przez pojedynczy słownik zasobów. Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Poniżej przedstawiono sposób pobierania zasobów zakresu aplikacji z słownika zasobów udostępnianych przez <xref:System.Windows.Application.Resources%2A> w języku XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Poniżej pokazano, jak można także uzyskać zasoby w kodzie.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Istnieją dwa kwestie, które należy wziąć pod uwagę podczas korzystania z <xref:System.Windows.Application.Resources%2A>. Najpierw *klucz* słownika jest obiektem, dlatego należy użyć dokładnie tego samego wystąpienia obiektu, gdy oba ustawienia i pobierają wartość właściwości. (Należy pamiętać, że podczas korzystania z ciągu w kluczu jest rozróżniana wielkość liter). Po drugie, *wartość* słownika jest obiektem, dlatego konieczne będzie przekonwertowanie wartości na żądany typ podczas pobierania wartości właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Połączone słowniki zasobów](../advanced/merged-resource-dictionaries.md)
