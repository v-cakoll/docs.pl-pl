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
ms.openlocfilehash: 192ac28610f596bc6b6f4ebf1c80962ab2d71cbf
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580536"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], program .NET Framework zawiera zestaw odbicia typów i elementów członkowskich do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Te typy i składowe dostępnych w pełny program .NET Framework oraz jak w [.NET for Windows Store apps](https://go.microsoft.com/fwlink/?LinkID=225700). W tym dokumencie opisano najważniejsze różnice między te i ich odpowiedniki w .NET Framework 4 i starszych wersji.  
  
 Jeśli tworzysz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, należy użyć odbicia, typy i elementy członkowskie w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Te typy i elementy członkowskie są również dostępne, ale nie jest to wymagane, do użytku w aplikacjach komputerowych, aby można było używać tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], <xref:System.Reflection.TypeInfo> klasa zawiera niektóre funkcje programu .NET Framework 4 <xref:System.Type> klasy. A <xref:System.Type> obiekt reprezentuje odwołanie do definicji typu, natomiast <xref:System.Reflection.TypeInfo> obiekt reprezentuje definicji typu. Dzięki temu można manipulować <xref:System.Type> obiektów bez niekoniecznie środowiska uruchomieniowego do załadowania zestawu odwołują. Wprowadzenie skojarzonego <xref:System.Reflection.TypeInfo> obiektu wymusza zestawu do załadowania.  
  
 <xref:System.Reflection.TypeInfo> zawiera wiele elementów członkowskich, które są dostępne na <xref:System.Type>oraz wielu właściwości odbicia w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] zwracają kolekcje <xref:System.Reflection.TypeInfo> obiektów. Aby uzyskać <xref:System.Reflection.TypeInfo> obiektu z <xref:System.Type> obiektu, należy użyć <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> metody.  
  
## <a name="query-methods"></a>Metody zapytań  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], można użyć właściwości odbicia, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcji zamiast metody, które zwracają tablice. Konteksty odbicia można zaimplementować przejście z opóźnieniem przez te kolekcje dla dużych zespołów lub typów.  
  
 Właściwości odbicia zwracać tylko metod zadeklarowanych w obiekcie zamiast przechodzić przez drzewo dziedziczenia. Ponadto nie używają <xref:System.Reflection.BindingFlags> parametry do filtrowania. Zamiast tego filtrowanie odbywa się w kodzie użytkownika za pomocą zapytań LINQ w kolekcjach zwrócone. Dla obiektów odbicia, które pochodzą ze środowiskiem uruchomieniowym (na przykład w wyniku `typeof(Object)`), przechodzenie przez drzewo dziedziczenia najlepiej odbywa się przy użyciu metody pomocnika <xref:System.Reflection.RuntimeReflectionExtensions> klasy. Konsumentów obiektów z kontekstów dostosowane odbicia nie można używać tych metod, a musi przechodzić przez drzewo dziedziczenia samodzielnie.  
  
## <a name="restrictions"></a>Ograniczenia  
 W [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, dostęp do niektórych typów programu .NET Framework i elementów członkowskich jest ograniczona. Na przykład nie można wywołać metody .NET Framework, które nie są uwzględnione w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], za pomocą <xref:System.Reflection.MethodInfo> obiektu. W dodatku, niektórych typów i elementów członkowskich, które nie są uznawane za bezpieczne w kontekście [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji są zablokowane, ponieważ są <xref:System.Runtime.InteropServices.Marshal> i <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> elementów członkowskich. To ograniczenie dotyczy tylko typów programu .NET Framework i elementów członkowskich; można wywołać kodu lub kodu innych firm, tak jak zwykle.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto odbicia, typy i elementy członkowskie w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] do pobrania, metod i właściwości <xref:System.Globalization.Calendar> typu, w tym właściwości i metody dziedziczone. Aby uruchomić ten kod, wklej go do pliku kodu dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] strony, która zawiera [Windows.UI.Xaml.Controls.Textblock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu o nazwie `textblock1` w projekcie o nazwie odbicia. Po wklejeniu tego kodu w projekcie o innej nazwie, po prostu upewnij się, że możesz zmienić nazwę przestrzeni nazw, aby dopasować projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Aplikacje .NET for Windows Store — obsługiwane interfejsy API](https://go.microsoft.com/fwlink/?LinkID=225700)
