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
ms.openlocfilehash: c9edab859900bf2001956045a5285801bb61d310
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045937"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store
Począwszy od .NET Framework 4,5, .NET Framework zawiera zestaw typów odbicia i elementów członkowskich do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacjach. Te typy i elementy członkowskie są dostępne w pełnej .NET Framework a także w programie [.NET dla aplikacji ze sklepu Windows](https://go.microsoft.com/fwlink/?LinkID=225700). W tym dokumencie wyjaśniono główne różnice między tymi i ich odpowiednikami w .NET Framework 4 i wcześniejszych wersjach.  
  
 W przypadku tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji należy użyć typów odbicia i elementów członkowskich w. [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Te typy i elementy członkowskie są również dostępne, ale nie są wymagane do użycia w aplikacjach klasycznych, dlatego można użyć tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]W <xref:System.Type> , Klasazawieraniektórefunkcjeklasy.NETFramework4.<xref:System.Reflection.TypeInfo> Obiekt reprezentuje odwołanie do definicji typu, <xref:System.Reflection.TypeInfo> natomiast obiekt reprezentuje definicję typu. <xref:System.Type> Dzięki temu można manipulować <xref:System.Type> obiektami bez konieczności wymagania środowiska uruchomieniowego do załadowania zestawu, do którego się odwołuje. Pobranie skojarzonego <xref:System.Reflection.TypeInfo> obiektu wymusza załadowanie zestawu.  
  
 <xref:System.Reflection.TypeInfo>zawiera wiele elementów członkowskich dostępnych w <xref:System.Type>i wiele właściwości odbicia [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] w kolekcjach <xref:System.Reflection.TypeInfo> zwracanych obiektów. Aby uzyskać <xref:System.Reflection.TypeInfo> obiekt <xref:System.Type> z obiektu, użyj <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> metody.  
  
## <a name="query-methods"></a>Metody zapytań  
 W, należy użyć właściwości odbicia, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje zamiast metod zwracających tablice. [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Konteksty odbicia mogą implementować przechodzenie z opóźnieniem tych kolekcji dla dużych zestawów lub typów.  
  
 Właściwości odbicia zwracają tylko zadeklarowane metody dla określonego obiektu zamiast przechodzenia przez drzewo dziedziczenia. Ponadto nie używają <xref:System.Reflection.BindingFlags> parametrów do filtrowania. Zamiast tego Filtrowanie odbywa się w kodzie użytkownika, przy użyciu zapytań LINQ dla zwracanych kolekcji. W przypadku obiektów odbicia, które pochodzą z środowiska uruchomieniowego (na przykład w wyniku `typeof(Object)`), przechodzenie drzewa dziedziczenia jest najlepiej realizowane przy użyciu metod <xref:System.Reflection.RuntimeReflectionExtensions> pomocnika klasy. Odbiorcy obiektów z niestandardowych kontekstów odbicia nie mogą korzystać z tych metod i muszą przechodzić przez drzewo dziedziczenia.  
  
## <a name="restrictions"></a>Ograniczenia  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] W aplikacji dostęp do niektórych typów .NET Framework i członków jest ograniczony. Na przykład nie można wywoływać metod .NET Framework, które nie są uwzględnione [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]w, <xref:System.Reflection.MethodInfo> przy użyciu obiektu. Ponadto niektóre typy i elementy członkowskie, które nie są uznawane za bezpieczne w kontekście [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, są blokowane, ponieważ są <xref:System.Runtime.InteropServices.Marshal> i <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> członkami. To ograniczenie dotyczy tylko typów .NET Framework i członków; Możesz wywołać kod lub kod innej firmy, jak zwykle.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano typy odbicia i elementy [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Członkowskie w programie, aby pobrać metody i <xref:System.Globalization.Calendar> właściwości typu, w tym dziedziczone metody i właściwości. Aby uruchomić ten kod, wklej go do pliku kodu dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] strony <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> zawierającej kontrolkę o nazwie `textblock1` w projekcie o nazwie odbicie. Jeśli wkleisz ten kod wewnątrz projektu o innej nazwie, upewnij się, że zmienisz nazwę przestrzeni nazw tak, aby pasowała do projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie](reflection.md)
- [.NET dla aplikacji ze sklepu Windows — obsługiwane interfejsy API](https://go.microsoft.com/fwlink/?LinkID=225700)
