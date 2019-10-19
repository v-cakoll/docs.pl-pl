---
title: -opcji refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582871"
---
# <a name="-refout-visual-basic"></a>-opcji refout (Visual Basic)

Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

`filepath`  
Ścieżka i nazwa pliku zestawu odwołania. Zwykle powinien znajdować się w podfolderze podstawowego zestawu. Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu. Wszystkie foldery w `filepath` muszą istnieć; Kompilator nie tworzy ich.

## <a name="remarks"></a>Uwagi

Visual Basic obsługuje przełącznik `-refout`, zaczynając od wersji 15,3.

Zestawy referencyjne są zestawami zawierającymi tylko metadane, które zawierają metadane, ale nie mają kodu implementacji. Zawierają one informacje o typie i elemencie członkowskim dla wszystkiego, z wyjątkiem typów anonimowych. Ich treści metod są zastępowane pojedynczą instrukcją `throw null`. Przyczyną użycia `throw null` metod treści (w przeciwieństwie do braku treści) jest to, że PEVerify może być uruchomiona i zakończyła się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).

Zestawy referencyjne zawierają atrybut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na poziomie zestawu. Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy). Ze względu na ten atrybut środowiska uruchomieniowe odmawiają załadowania zestawów referencyjnych na potrzeby wykonywania (ale nadal mogą być ładowane w kontekście "tylko odbicie"). Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako odbicie. w przeciwnym razie środowisko uruchomieniowe zgłosi <xref:System.BadImageFormatException>.

Opcje `-refout` i [`-refonly`](refonly-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz także

- [-refonly](refonly-compiler-option.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
