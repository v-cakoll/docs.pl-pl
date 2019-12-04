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
ms.openlocfilehash: d68f406b704df905528d444b605681ca6e871127
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714440"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Odbicia w .NET Framework dla aplikacji sklepu Windows Store

Począwszy od .NET Framework 4,5, .NET Framework obejmuje zestaw typów odbicia i elementów członkowskich do użycia w aplikacjach do sklepu Windows 8. x. Te typy i elementy członkowskie są dostępne w pełnej .NET Framework a także w programie .NET dla aplikacji ze sklepu Windows. W tym dokumencie wyjaśniono główne różnice między tymi i ich odpowiednikami w .NET Framework 4 i wcześniejszych wersjach.  
  
 Jeśli tworzysz aplikację ze sklepu Windows 8. x, musisz użyć typów odbicia i elementów członkowskich w aplikacjach ze sklepu .NET dla systemu Windows 8. x. Te typy i elementy członkowskie są również dostępne, ale nie są wymagane do użycia w aplikacjach klasycznych, dlatego można użyć tego samego kodu dla obu typów aplikacji.  
  
## <a name="typeinfo-and-assembly-loading"></a>Klasa TypeInfo i ładowanie zestawu  
 W aplikacji ze sklepu .NET dla systemu Windows 8. x, Klasa <xref:System.Reflection.TypeInfo> zawiera niektóre funkcje klasy <xref:System.Type> .NET Framework 4. Obiekt <xref:System.Type> reprezentuje odwołanie do definicji typu, natomiast obiekt <xref:System.Reflection.TypeInfo> reprezentuje definicję typu. Dzięki temu można manipulować obiektami <xref:System.Type> bez konieczności wymagania środowiska uruchomieniowego do załadowania zestawu, do którego się odwołuje. Pobieranie skojarzonego obiektu <xref:System.Reflection.TypeInfo> wymusza załadowanie zestawu.  
  
 <xref:System.Reflection.TypeInfo> zawiera wiele elementów członkowskich dostępnych w <xref:System.Type>i wiele właściwości odbicia w aplikacjach do sklepu .NET dla systemu Windows 8. x zwraca kolekcje obiektów <xref:System.Reflection.TypeInfo>. Aby uzyskać <xref:System.Reflection.TypeInfo> obiekt z obiektu <xref:System.Type>, użyj metody <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Metody zapytań  
 W aplikacjach ze sklepu .NET dla systemu Windows 8. x należy użyć właściwości odbicia, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje zamiast metod, które zwracają tablice. Konteksty odbicia mogą implementować przechodzenie z opóźnieniem tych kolekcji dla dużych zestawów lub typów.  
  
 Właściwości odbicia zwracają tylko zadeklarowane metody dla określonego obiektu zamiast przechodzenia przez drzewo dziedziczenia. Ponadto nie używają parametrów <xref:System.Reflection.BindingFlags> do filtrowania. Zamiast tego Filtrowanie odbywa się w kodzie użytkownika, przy użyciu zapytań LINQ dla zwracanych kolekcji. W przypadku obiektów odbicia, które pochodzą z środowiska uruchomieniowego (na przykład w wyniku `typeof(Object)`), przechodzenie drzewa dziedziczenia jest najlepiej realizowane przy użyciu metod pomocnika klasy <xref:System.Reflection.RuntimeReflectionExtensions>. Odbiorcy obiektów z niestandardowych kontekstów odbicia nie mogą korzystać z tych metod i muszą przechodzić przez drzewo dziedziczenia.  
  
## <a name="restrictions"></a>{1&gt;Ograniczenia&lt;1}  
 W aplikacji ze sklepu Windows 8. x dostęp do niektórych typów .NET Framework i członków jest ograniczony. Nie można na przykład wywoływać .NET Framework metod, które nie są uwzględnione w programie .NET dla aplikacji ze sklepu Windows 8. x za pomocą obiektu <xref:System.Reflection.MethodInfo>. Ponadto niektóre typy i elementy członkowskie, które nie są uznawane za bezpieczne w kontekście aplikacji ze sklepu Windows 8. x, są blokowane, ponieważ <xref:System.Runtime.InteropServices.Marshal> i <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> członków. To ograniczenie dotyczy tylko typów .NET Framework i członków; Możesz wywołać kod lub kod innej firmy, jak zwykle.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano typy odbicia i elementy członkowskie w aplikacji ze sklepu .NET dla systemu Windows 8. x, aby pobrać metody i właściwości typu <xref:System.Globalization.Calendar>, w tym dziedziczone metody i właściwości. Aby uruchomić ten kod, wklej go do pliku kodu dla strony sklepu Windows 8. x, która zawiera kontrolkę <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> o nazwie `textblock1` w projekcie o nazwie odbicie. Jeśli wkleisz ten kod wewnątrz projektu o innej nazwie, upewnij się, że zmienisz nazwę przestrzeni nazw tak, aby pasowała do projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie](reflection.md)
