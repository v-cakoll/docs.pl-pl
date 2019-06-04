---
title: Równoważność typów i osadzone typy międzyoperacyjne
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 137aeaab4e63adbb81c0f3d90718def10f906e6a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489236"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Równoważność typów i osadzone typy międzyoperacyjne

Począwszy od programu .NET Framework 4 środowisko uruchomieniowe języka wspólnego obsługuje osadzanie informacji o typie dla typów modelu COM bezpośrednio do zestawów zarządzanych, zamiast zestawów zarządzanych uzyskać informacje o typie dla typów modelu COM z zestawów międzyoperacyjnych. Informacje o typie osadzony zawiera tylko typy i elementy członkowskie, które są rzeczywiście używane przez zestaw zarządzany, dwóch zestawów zarządzanych, może być bardzo różne widoki tego samego typu COM. Każdy zestaw zarządzany ma inną <xref:System.Type> obiektu do reprezentowania jej widok typów modelu COM. Środowisko uruchomieniowe języka wspólnego obsługuje równoważności typu między te różne widoki dla interfejsy, struktury, wyliczenia i delegaty.

Równoważności typu oznacza o tym, że obiekt COM, który jest przekazywany z jednego zestawu zarządzanego do innego, mogą być rzutowane do odpowiedniego zarządzane typu w zestawie odbierania.

> [!NOTE]
> Równoważność typów i osadzone typy międzyoperacyjne we wdrażaniu aplikacji i dodatki, które korzystają ze składników COM, ponieważ nie jest wymagane do wdrożenia usług międzyoperacyjnych z aplikacjami. Deweloperzy udostępnionych składników modelu COM nadal jest konieczne tworzenie podstawowych zestawów międzyoperacyjnych (PIA), jeśli chcą, aby ich składniki do użycia przez starsze wersje programu .NET Framework.

## <a name="type-equivalence"></a>Odpowiednik typu

 Równoważność typów modelu COM, jest obsługiwana dla interfejsy, struktury, wyliczenia i delegaty. Typy modelu COM kwalifikują się jako równoważne, jeśli spełnione są wszystkie z następujących czynności:

- Typy są zarówno interfejsów, lub zarówno struktur, lub zarówno wyliczenia lub obu delegatów.

- Typy mają taką samą tożsamość, zgodnie z opisem w następnej sekcji.

- Oba typy kwalifikują się do typu równoważności, zgodnie z opisem w [oznaczanie typy modelu COM dla równoważności typu](#marking-com-types-for-type-equivalence) sekcji.

### <a name="type-identity"></a>Typ tożsamości

Dwa typy są określane za tej samej tożsamości, gdy ich zakresów i tożsamości są zgodne, oznacza to, jeśli każda z nich <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut i dwa atrybuty zawierają zgodnych <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> i <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości. Porównanie dla <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> jest rozróżniana wielkość liter.

Jeśli typ nie ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut, lub jeśli ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybut, który nie określa zakresu i identyfikator, typ mogą nadal zostać uwzględnione w równoważności w następujący sposób:

- W przypadku interfejsów wartość <xref:System.Runtime.InteropServices.GuidAttribute> jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> właściwości i <xref:System.Type.FullName%2A?displayProperty=nameWithType> (czyli nazwę typu, włącznie z przestrzenią nazw) jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> właściwości.

- Dla struktury, wyliczenia i delegaci <xref:System.Runtime.InteropServices.GuidAttribute> zestawu zawierającego jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> właściwości i <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwość jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości.

### <a name="marking-com-types-for-type-equivalence"></a>Oznaczanie typów modelu COM dla równoważności typu

 Można oznaczyć typu jako kwalifikuje się do równoważności typu na dwa sposoby:

- Zastosuj <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu typu.

- Zmień typ typ importu COM. Interfejs jest typ importu COM, jeśli ma on <xref:System.Runtime.InteropServices.ComImportAttribute> atrybutu. Interfejs, struktury, wyliczenia lub delegata jest typ importu COM, jeśli zestaw, w którym jest zdefiniowana ma <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atrybutu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Type.IsEquivalentTo%2A>
- [Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
