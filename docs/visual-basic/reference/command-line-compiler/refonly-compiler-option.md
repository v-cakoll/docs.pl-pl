---
title: -jest opcja SET refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932666"
---
# <a name="-refonly-visual-basic"></a>-jest opcja SET refonly (Visual Basic)

**Jest opcja refonly -** opcja wskazuje, że główny wynik kompilacji należy zamiast zestawu implementacji zestawu odwołania. `-refonly` Parametr dyskretnie wyłącza podawania plików PDB, ponieważ zestawy odwołań nie można wykonać.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refonly
```

## <a name="remarks"></a>Uwagi

Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15.3.

Zestawy referencyjne są tylko metadane zestawów, które zawierają metadane, ale bez kodu realizacji. Obejmują one informacje typów i elementów członkowskich dla wszystkim, z wyjątkiem typów anonimowych. Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).

Zestawy referencyjne zawierają poziomie zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu. Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania). Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w kontekstu reflection-only). Narzędzia, które odzwierciedlają zestawów, należy upewnić się, że są one ładowane odwołań do zestawów jako tylko do odbicia. w przeciwnym wypadku środowisko wykonawcze zgłasza <xref:System.BadImageFormatException>.

`-refonly` i [ `-refout` ](refout-compiler-option.md) opcje wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także
[-opcji refout](refout-compiler-option.md)   
[Kompilator wiersza polecenia programu Visual Basic](index.md)  
[Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)   
