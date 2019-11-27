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
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448131"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store

Począwszy od .NET Framework 4,5, .NET Framework obejmuje zestaw typów odbicia i elementów członkowskich do użycia w aplikacjach do sklepu Windows 8. x. Te typy i elementy członkowskie są dostępne w pełnej .NET Framework a także w programie .NET dla aplikacji ze sklepu Windows. W tym dokumencie wyjaśniono główne różnice między tymi i ich odpowiednikami w .NET Framework 4 i wcześniejszych wersjach.  
  
 Jeśli tworzysz aplikację ze sklepu Windows 8. x, musisz użyć typów odbicia i elementów członkowskich w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Te typy i elementy członkowskie są również dostępne, ale nie są wymagane do użycia w aplikacjach klasycznych, dlatego można użyć tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]Klasa <xref:System.Reflection.TypeInfo> zawiera niektóre funkcje klasy <xref:System.Type> .NET Framework 4. Obiekt <xref:System.Type> reprezentuje odwołanie do definicji typu, natomiast obiekt <xref:System.Reflection.TypeInfo> reprezentuje definicję typu. Dzięki temu można manipulować obiektami <xref:System.Type> bez konieczności wymagania środowiska uruchomieniowego do załadowania zestawu, do którego się odwołuje. Pobieranie skojarzonego obiektu <xref:System.Reflection.TypeInfo> wymusza załadowanie zestawu.  
  
 <xref:System.Reflection.TypeInfo> zawiera wiele elementów członkowskich dostępnych na <xref:System.Type>i wiele właściwości odbicia w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Zwróć kolekcje obiektów <xref:System.Reflection.TypeInfo>. Aby uzyskać <xref:System.Reflection.TypeInfo> obiekt z obiektu <xref:System.Type>, użyj metody <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Metody zapytań  
 W [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]Użyj właściwości odbicia, które zwracają kolekcje <xref:System.Collections.Generic.IEnumerable%601> zamiast metod zwracających tablice. Konteksty odbicia mogą implementować przechodzenie z opóźnieniem tych kolekcji dla dużych zestawów lub typów.  
  
 Właściwości odbicia zwracają tylko zadeklarowane metody dla określonego obiektu zamiast przechodzenia przez drzewo dziedziczenia. Ponadto nie używają parametrów <xref:System.Reflection.BindingFlags> do filtrowania. Zamiast tego Filtrowanie odbywa się w kodzie użytkownika, przy użyciu zapytań LINQ dla zwracanych kolekcji. W przypadku obiektów odbicia, które pochodzą z środowiska uruchomieniowego (na przykład w wyniku `typeof(Object)`), przechodzenie drzewa dziedziczenia jest najlepiej realizowane przy użyciu metod pomocnika klasy <xref:System.Reflection.RuntimeReflectionExtensions>. Odbiorcy obiektów z niestandardowych kontekstów odbicia nie mogą korzystać z tych metod i muszą przechodzić przez drzewo dziedziczenia.  
  
## <a name="restrictions"></a>Ograniczenia  
 W aplikacji ze sklepu Windows 8. x dostęp do niektórych typów .NET Framework i członków jest ograniczony. Nie można na przykład wywoływać .NET Framework metod, które nie są uwzględnione w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], przy użyciu obiektu <xref:System.Reflection.MethodInfo>. Ponadto niektóre typy i elementy członkowskie, które nie są uznawane za bezpieczne w kontekście aplikacji ze sklepu Windows 8. x, są blokowane, ponieważ <xref:System.Runtime.InteropServices.Marshal> i <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> członków. To ograniczenie dotyczy tylko typów .NET Framework i członków; Możesz wywołać kod lub kod innej firmy, jak zwykle.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano typy odbicia i elementy członkowskie w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], aby pobrać metody i właściwości typu <xref:System.Globalization.Calendar>, w tym dziedziczone metody i właściwości. Aby uruchomić ten kod, wklej go do pliku kodu dla strony sklepu Windows 8. x, która zawiera kontrolkę <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> o nazwie `textblock1` w projekcie o nazwie odbicie. Jeśli wkleisz ten kod wewnątrz projektu o innej nazwie, upewnij się, że zmienisz nazwę przestrzeni nazw tak, aby pasowała do projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie](reflection.md)
