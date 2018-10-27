---
title: -opcji refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 8a8068c467f9066af3153434187749fa80d254ca
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048401"
---
# <a name="-refout-visual-basic"></a>-opcji refout (Visual Basic)

**- Opcji refout** opcja określa ścieżkę pliku, gdzie zestaw odwołania powinny być danych wyjściowych.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath` Ścieżka i nazwa pliku zestawu odwołania. Ogólnie należy się w podfolderze podstawowego zestawu. Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolder względem podstawowego zestawu. Wszystkie foldery w `filepath` musi istnieć; kompilator nie tworzy je. 

## <a name="remarks"></a>Uwagi

Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15.3.

Zestawy referencyjne są tylko metadane zestawów, które zawierają metadane, ale bez kodu realizacji. Obejmują one informacje typów i elementów członkowskich dla wszystkim, z wyjątkiem typów anonimowych. Ich treść metody są zastępowane za pomocą jednego `throw null` instrukcji. Przyczyna przy użyciu `throw null` treści metod (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).

Zestawy referencyjne zawierają poziomie zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu. Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania). Z powodu tego atrybutu środowisk wykonawczych odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w kontekstu reflection-only). Narzędzia, które odzwierciedlają zestawów, należy upewnić się, że są one ładowane odwołań do zestawów jako tylko do odbicia. w przeciwnym wypadku środowisko wykonawcze zgłasza <xref:System.BadImageFormatException>.

`-refout` i [ `-refonly` ](refonly-compiler-option.md) opcje wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz też
[-jest opcja refonly](refonly-compiler-option.md)   
[Kompilator wiersza polecenia programu Visual Basic](index.md)  
[Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)  

