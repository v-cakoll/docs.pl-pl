---
title: Odbicia w .NET Framework dla aplikacji sklepu Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 598acd746949369ffec7d153b6870bebeeafe532
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398794"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], .NET Framework zawiera zestaw odbicia typów i członków do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Te typy i składniki są dostępne w pełnej .NET Framework oraz jak w [.NET dla Sklepu Windows apps](http://go.microsoft.com/fwlink/?LinkID=225700). W tym dokumencie opisano główne różnice między te i ich odpowiedniki w .NET Framework 4 i starszych wersji.  
  
 Jeśli tworzysz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, należy użyć odbicia typów i członków [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Te typy i składniki są również dostępne, ale nie jest to wymagane, do użycia w aplikacjach klasycznych, dzięki czemu można użyć tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], <xref:System.Reflection.TypeInfo> klasa zawiera niektóre funkcje programu .NET Framework 4 <xref:System.Type> klasy. A <xref:System.Type> obiekt reprezentuje odwołanie do definicji typu, podczas gdy <xref:System.Reflection.TypeInfo> obiekt reprezentuje samą definicję typu. Dzięki temu można manipulować <xref:System.Type> obiektów bez konieczności musi załadować zestawu odwołują się do środowiska uruchomieniowego. Pobieranie skojarzony <xref:System.Reflection.TypeInfo> obiektu wymusza zestawu do załadowania.  
  
 <xref:System.Reflection.TypeInfo> zawiera wiele elementów członkowskich na <xref:System.Type>i wiele właściwości odbicia w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] zwracać kolekcji <xref:System.Reflection.TypeInfo> obiektów. Aby uzyskać <xref:System.Reflection.TypeInfo> obiekt z <xref:System.Type> obiektów, użyj <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> metody.  
  
## <a name="query-methods"></a>Metody zapytania  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], użyj właściwości odbicia, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje zamiast metody zwracające tablice. Konteksty odbicia można zaimplementować opóźnieniem przechodzenie tych kolekcji dla dużych zestawów lub typów.  
  
 Właściwości odbicia zwracać tylko metody zadeklarowanej dla określonego obiektu zamiast przechodzenie drzewa dziedziczenia. Ponadto nie używają <xref:System.Reflection.BindingFlags> parametry do filtrowania. Zamiast tego filtrowania odbywa się w kodzie użytkownika przy użyciu zapytań LINQ w kolekcjach zwrócony. Dla obiektów odbicia, które pochodzą ze środowiskiem uruchomieniowym (na przykład w wyniku `typeof(Object)`), przeglądanie drzewa dziedziczenia najlepiej odbywa się przy użyciu metody pomocnika <xref:System.Reflection.RuntimeReflectionExtensions> klasy. Konsumenci obiektów z dostosowane konteksty odbicia nie można użyć tych metod i musi przechodzić przez drzewa dziedziczenia samodzielnie.  
  
## <a name="restrictions"></a>Ograniczenia  
 W [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, dostęp do niektórych typów .NET Framework i elementów członkowskich jest ograniczony. Na przykład nie można wywoływać metod .NET Framework, które nie znajdują się w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], za pomocą <xref:System.Reflection.MethodInfo> obiektu. W dodatku, niektórych typów i elementów członkowskich, które nie są uznawane za bezpieczne w kontekście [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji są zablokowane, ponieważ są <xref:System.Runtime.InteropServices.Marshal> i <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> elementów członkowskich. To ograniczenie dotyczy tylko typy .NET Framework i członków; można wywołać z kodu lub kodu innych firm w zwykły sposób.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używane odbicia typów i członków [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] można pobrać metody i właściwości <xref:System.Globalization.Calendar> typu, w tym dziedziczonej metody i właściwości. Aby uruchomić ten kod, wklej go do pliku kodu dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] strona zawierająca [Windows.UI.Xaml.Controls.Textblock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu o nazwie `textblock1` w projekcie o nazwie odbicia. Tylko po wklejeniu tego kodu wewnątrz projektu o innej nazwie, upewnij się, że Zmień nazwę przestrzeni nazw do dopasowania projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [.NET dla Sklepu Windows apps — obsługiwanych interfejsów API](http://go.microsoft.com/fwlink/?LinkID=225700)
