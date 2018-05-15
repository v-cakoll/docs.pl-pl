---
title: -deterministyczna
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb1d27f614afc3b07f9d663831fc2071535236f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-deterministic"></a><span data-ttu-id="b0435-102">-deterministyczna</span><span class="sxs-lookup"><span data-stu-id="b0435-102">-deterministic</span></span>

<span data-ttu-id="b0435-103">Powoduje, że kompilator, aby utworzyć zestaw, której wyjście bajtów dla bajtów jest identyczne w kompilacji dla identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b0435-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="b0435-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0435-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="b0435-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0435-105">Remarks</span></span>

<span data-ttu-id="b0435-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator dodaje znacznikiem czasu i identyfikatorem GUID, który jest generowany na podstawie liczby losowe.</span><span class="sxs-lookup"><span data-stu-id="b0435-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="b0435-107">Możesz użyć `-deterministic` opcję, aby utworzyć *deterministyczne zestawu*, jedną z którego zawartość binarna jest identyczne w kompilacji, tak długo, jak dane wejściowe jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="b0435-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="b0435-108">Kompilator uwzględnia następujące dane wejściowe na potrzeby determinizm:</span><span class="sxs-lookup"><span data-stu-id="b0435-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="b0435-109">Sekwencja parametry wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b0435-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="b0435-110">Zawartość pliku odpowiedzi .rsp — kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b0435-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="b0435-111">Dokładne wersja kompilatora używane i jego zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="b0435-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="b0435-112">Ścieżka bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b0435-112">The current directory path.</span></span>
- <span data-ttu-id="b0435-113">Wszystkie pliki binarne treści jawnie przekazany do kompilatora bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="b0435-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span> 
    - <span data-ttu-id="b0435-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="b0435-114">Source files</span></span>
    - <span data-ttu-id="b0435-115">przywoływanych zestawach</span><span class="sxs-lookup"><span data-stu-id="b0435-115">Referenced assemblies</span></span>
    - <span data-ttu-id="b0435-116">Przywoływany modułów</span><span class="sxs-lookup"><span data-stu-id="b0435-116">Referenced modules</span></span>
    - <span data-ttu-id="b0435-117">Zasoby</span><span class="sxs-lookup"><span data-stu-id="b0435-117">Resources</span></span>
    - <span data-ttu-id="b0435-118">Plik klucza silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="b0435-118">The strong name key file</span></span>
    - <span data-ttu-id="b0435-119">@ pliki odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="b0435-119">@ response files</span></span>
    - <span data-ttu-id="b0435-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="b0435-120">Analyzers</span></span>
    - <span data-ttu-id="b0435-121">Zestawy reguł</span><span class="sxs-lookup"><span data-stu-id="b0435-121">Rulesets</span></span>
    - <span data-ttu-id="b0435-122">Dodatkowe pliki, które mogą być używane przez analizatory</span><span class="sxs-lookup"><span data-stu-id="b0435-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="b0435-123">Bieżąca kultura (język, w którym diagnostyki i wyjątków są produkowane wiadomości).</span><span class="sxs-lookup"><span data-stu-id="b0435-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="b0435-124">Domyślnym kodowaniem (lub bieżącej stronie kodowej) Jeśli nie określono kodowanie.</span><span class="sxs-lookup"><span data-stu-id="b0435-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="b0435-125">Istnienie, brak i zawartość plików w ścieżkach wyszukiwania przez kompilator (określonej, na przykład przez `/lib` lub `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="b0435-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="b0435-126">Platforma CLR, na którym jest wykonywane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="b0435-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="b0435-127">Wartość `%LIBPATH%`, co może wpłynąć na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="b0435-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="b0435-128">Gdy publicznie dostępnych źródeł, kompilacji deterministycznej może służyć do ustalenia, czy dane binarne ma być kompilowana z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="b0435-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="b0435-129">Może być również przydatne w systemie kompilacji ciągłej do określenia, czy konieczne można wykonać kroki procesu kompilacji, które są zależne od zmian w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="b0435-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="b0435-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0435-130">See Also</span></span>
[<span data-ttu-id="b0435-131">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0435-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
[<span data-ttu-id="b0435-132">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="b0435-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
