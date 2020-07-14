---
title: Równoważność typów i osadzone typy międzyoperacyjnych
description: Zrozumienie równoważności typu między typami .NET i elementami członkowskimi z zestawem zarządzanym i typami COM, które są osadzone w tym zestawie. Dla platformy .NET 4 i nowszych.
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: 2d572133c42f01af7d50f6f771588f5173853f9a
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282011"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Równoważność typów i osadzone typy międzyoperacyjnych

Począwszy od .NET Framework 4, środowisko uruchomieniowe języka wspólnego obsługuje osadzanie informacji o typach COM bezpośrednio w zarządzanych zestawach, a nie wymaga, aby zestawy zarządzane uzyskały informacje o typie dla typów COM z zestawów międzyoperacyjnych. Ponieważ informacje o typie osadzonym zawierają tylko typy i elementy członkowskie, które są faktycznie używane przez zarządzany zestaw, dwa zarządzane zestawy mogą mieć bardzo różne widoki tego samego typu COM. Każdy zarządzany zestaw ma inny <xref:System.Type> obiekt reprezentujący jego widok typu com. Środowisko uruchomieniowe języka wspólnego obsługuje równoważność typu między tymi różnymi widokami dla interfejsów, struktur, wyliczeń i delegatów.

Równoważność typu oznacza, że obiekt COM, który jest przesyłany z jednego zarządzanego zestawu do innego, może być rzutowany na odpowiedni typ zarządzany w zestawie do odbioru.

> [!NOTE]
> Równoważność typów i osadzone typy międzyoperacyjny upraszczają wdrażanie aplikacji i dodatków korzystających ze składników modelu COM, ponieważ nie jest to konieczne do wdrażania zestawów międzyoperacyjnych w aplikacjach. Deweloperzy udostępnionych składników COM nadal muszą utworzyć podstawowe zestawy międzyoperacyjności (zestawów PIA), jeśli chcą, aby ich składniki były używane przez wcześniejsze wersje .NET Framework.

## <a name="type-equivalence"></a>Równoważność typu

 Równoważność typów COM jest obsługiwana dla interfejsów, struktur, wyliczeń i delegatów. Typy COM kwalifikują się jako równoważne, jeśli spełnione są wszystkie następujące warunki:

- Typy są zarówno interfejsami, jak i zarówno strukturami, jak i zarówno wyliczeniami, jak i obu delegatów.

- Typy mają taką samą tożsamość, jak opisano w następnej sekcji.

- Oba typy kwalifikują się do równoważności typów, zgodnie z opisem w sekcji [oznaczanie typów com dla równoważności typów](#marking-com-types-for-type-equivalence) .

### <a name="type-identity"></a>Tożsamość typu

Dwa typy są określane jako mają tę samą tożsamość, gdy ich zakresy i tożsamości są zgodne, innymi słowy, jeśli każdy z nich ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut, a dwa atrybuty mają pasujące <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> i <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości. W porównaniu z <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> wielkością liter nie jest rozróżniana wielkość liter.

Jeśli typ nie ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu lub jeśli ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut, który nie określa zakresu i identyfikatora, typ można nadal rozważyć dla równoważności w następujący sposób:

- W przypadku interfejsów wartość <xref:System.Runtime.InteropServices.GuidAttribute> jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> właściwości, a <xref:System.Type.FullName%2A?displayProperty=nameWithType> Właściwość (czyli nazwa typu, w tym przestrzeń nazw) jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> właściwości.

- W przypadku struktur, wyliczeń i delegatów <xref:System.Runtime.InteropServices.GuidAttribute> zestaw zawierający jest używany zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> właściwości, a <xref:System.Type.FullName%2A?displayProperty=nameWithType> Właściwość jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości.

### <a name="marking-com-types-for-type-equivalence"></a>Oznaczanie typów COM dla równoważności typów

 Można oznaczyć typ jako kwalifikujący się do równoważności typów na dwa sposoby:

- Zastosuj <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut do typu.

- Oznacz typ typem importu COM. Interfejs jest typem importu COM, jeśli ma <xref:System.Runtime.InteropServices.ComImportAttribute> atrybut. Interfejs, struktura, Wyliczenie lub delegat jest typem importu COM, jeśli zestaw, w którym jest zdefiniowany, ma <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atrybut.

## <a name="see-also"></a>Zobacz także

- <xref:System.Type.IsEquivalentTo%2A>
- [Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
