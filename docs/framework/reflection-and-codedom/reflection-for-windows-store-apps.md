---
title: Odbicia w .NET Framework dla aplikacji sklepu Windows Store
description: Użyj odbicia w programie .NET dla aplikacji ze sklepu Windows. Istnieje zestaw typów odbicia i członków do użycia w aplikacjach ze sklepu Windows, które są dostępne dla pełnego programu .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
ms.openlocfilehash: 86bb633e97f0f88dc2a2a042b6897695a258cc3c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865271"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store

Począwszy od .NET Framework 4,5, .NET Framework obejmuje zestaw typów odbicia i elementów członkowskich do użycia w aplikacjach do sklepu Windows 8. x. Te typy i elementy członkowskie są dostępne w pełnej .NET Framework a także w programie .NET dla aplikacji ze sklepu Windows. W tym dokumencie wyjaśniono główne różnice między tymi i ich odpowiednikami w .NET Framework 4 i wcześniejszych wersjach.  
  
 Jeśli tworzysz aplikację ze sklepu Windows 8. x, musisz użyć typów odbicia i elementów członkowskich w aplikacjach ze sklepu .NET dla systemu Windows 8. x. Te typy i elementy członkowskie są również dostępne, ale nie są wymagane do użycia w aplikacjach klasycznych, dlatego można użyć tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 W aplikacji ze sklepu .NET dla systemu Windows 8. x, <xref:System.Reflection.TypeInfo> Klasa zawiera niektóre funkcje klasy .NET Framework 4 <xref:System.Type> . <xref:System.Type>Obiekt reprezentuje odwołanie do definicji typu, natomiast <xref:System.Reflection.TypeInfo> obiekt reprezentuje definicję typu. Dzięki temu można manipulować <xref:System.Type> obiektami bez konieczności wymagania środowiska uruchomieniowego do załadowania zestawu, do którego się odwołuje. Pobranie skojarzonego <xref:System.Reflection.TypeInfo> obiektu wymusza załadowanie zestawu.  
  
 <xref:System.Reflection.TypeInfo>zawiera wiele elementów członkowskich dostępnych w systemie <xref:System.Type> i wiele właściwości odbicia w aplikacjach do sklepu .NET dla systemu Windows 8. x zwraca kolekcje <xref:System.Reflection.TypeInfo> obiektów. Aby uzyskać <xref:System.Reflection.TypeInfo> obiekt z <xref:System.Type> obiektu, użyj <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> metody.  
  
## <a name="query-methods"></a>Metody zapytań  
 W aplikacjach ze sklepu .NET dla systemu Windows 8. x należy użyć właściwości odbicia, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje zamiast metod zwracających tablice. Konteksty odbicia mogą implementować przechodzenie z opóźnieniem tych kolekcji dla dużych zestawów lub typów.  
  
 Właściwości odbicia zwracają tylko zadeklarowane metody dla określonego obiektu zamiast przechodzenia przez drzewo dziedziczenia. Ponadto nie używają <xref:System.Reflection.BindingFlags> parametrów do filtrowania. Zamiast tego Filtrowanie odbywa się w kodzie użytkownika, przy użyciu zapytań LINQ dla zwracanych kolekcji. W przypadku obiektów odbicia, które pochodzą z środowiska uruchomieniowego (na przykład w wyniku `typeof(Object)` ), przechodzenie drzewa dziedziczenia jest najlepiej realizowane przy użyciu metod pomocnika <xref:System.Reflection.RuntimeReflectionExtensions> klasy. Odbiorcy obiektów z niestandardowych kontekstów odbicia nie mogą korzystać z tych metod i muszą przechodzić przez drzewo dziedziczenia.  
  
## <a name="restrictions"></a>Ograniczenia  
 W aplikacji ze sklepu Windows 8. x dostęp do niektórych typów .NET Framework i członków jest ograniczony. Nie można na przykład wywoływać .NET Framework metod, które nie są uwzględnione w programie .NET dla aplikacji ze sklepu Windows 8. x przy użyciu <xref:System.Reflection.MethodInfo> obiektu. Ponadto niektóre typy i elementy członkowskie, które nie są uznawane za bezpieczne w kontekście aplikacji ze sklepu Windows 8. x, są blokowane, jak <xref:System.Runtime.InteropServices.Marshal> i są <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> członkami. To ograniczenie dotyczy tylko typów .NET Framework i członków; Możesz wywołać kod lub kod innej firmy, jak zwykle.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano typy odbicia i elementy członkowskie w aplikacji ze sklepu .NET dla systemu Windows 8. x, aby pobrać metody i właściwości <xref:System.Globalization.Calendar> typu, w tym dziedziczone metody i właściwości. Aby uruchomić ten kod, wklej go do pliku kodu dla strony sklepu Windows 8. x, która zawiera <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> kontrolkę o nazwie `textblock1` w projekcie o nazwie odbicie. Jeśli wkleisz ten kod wewnątrz projektu o innej nazwie, upewnij się, że zmienisz nazwę przestrzeni nazw tak, aby pasowała do projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie](reflection.md)
