---
title: 'Instrukcje: Użyj słownika zasobów zakresu aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 6cd3e125b5b1a97f5851d4d1845e3e9e384e3d16
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748560"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Instrukcje: Użyj słownika zasobów zakresu aplikacji
Ten przykład pokazuje, jak zdefiniować i użyć słownika niestandardowego zasobów zakresu aplikacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Application> udostępnia magazyn zakresu aplikacji do zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A>. Domyślnie <xref:System.Windows.Application.Resources%2A> właściwość jest inicjowana z wystąpieniem <xref:System.Windows.ResourceDictionary> typu. Użycie tego wystąpienia, jeśli pobieranie i ustawianie właściwości zakresu aplikacji za pomocą <xref:System.Windows.Application.Resources%2A>. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie i ustawianie zasobów zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Jeśli masz wiele zasobów, które można ustawić za pomocą <xref:System.Windows.Application.Resources%2A>, można zamiast tego użyć słownika zasobów niestandardowych do przechowywania tych zasobów i ustawić <xref:System.Windows.Application.Resources%2A> z nim zamiast tego. Poniżej przedstawiono, jak zadeklarować słownik zasobów niestandardowych przy użyciu XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Wymiana całego zasobu słownikami przy użyciu <xref:System.Windows.Application.Resources%2A> umożliwiają obsługę motywów zakres aplikacji, gdzie każdy motyw jest hermetyzowany przez słownik pojedynczy zasób. Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Poniżej pokazano, jak można uzyskać zasobów zakresu aplikacji ze słownika zasobów udostępnianych przez <xref:System.Windows.Application.Resources%2A> w XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Poniżej przedstawiono, jak również zawiera zasoby w kodzie.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Istnieją dwie kwestie podczas korzystania z <xref:System.Windows.Application.Resources%2A>. Po pierwsze, słownika *klucza* jest obiektem, więc należy użyć dokładnie tego samego wystąpienia obiektu podczas ustawiania i pobierania wartości właściwości. (Zwróć uwagę, że klucz jest rozróżniana wielkość liter, przy użyciu ciągu). Drugi, słownika *wartość* jest obiektem, dlatego trzeba przekonwertować wartości na żądany typ podczas pobierania wartości właściwości.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Połączone słowniki zasobów](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
