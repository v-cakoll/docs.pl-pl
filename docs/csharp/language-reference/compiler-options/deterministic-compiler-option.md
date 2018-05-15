---
title: -deterministyczne (opcje kompilatora C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb45ea6ed5c5795c910b2f6c3575b12f8189cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-deterministic"></a><span data-ttu-id="5f3de-102">-deterministyczna</span><span class="sxs-lookup"><span data-stu-id="5f3de-102">-deterministic</span></span>

<span data-ttu-id="5f3de-103">Powoduje, że kompilator, aby utworzyć zestaw, której wyjście bajtów dla bajtów jest identyczne w kompilacji dla identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5f3de-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="5f3de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f3de-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="5f3de-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f3de-105">Remarks</span></span>

<span data-ttu-id="5f3de-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator dodaje znacznikiem czasu i identyfikatorem GUID, który jest generowany na podstawie liczby losowe.</span><span class="sxs-lookup"><span data-stu-id="5f3de-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="5f3de-107">Możesz użyć `-deterministic` opcję, aby utworzyć *deterministyczne zestawu*, jedną z którego zawartość binarna jest identyczne w kompilacji, tak długo, jak dane wejściowe jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="5f3de-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="5f3de-108">Kompilator uwzględnia następujące dane wejściowe na potrzeby determinizm:</span><span class="sxs-lookup"><span data-stu-id="5f3de-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="5f3de-109">Sekwencja parametry wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f3de-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="5f3de-110">Zawartość pliku odpowiedzi .rsp — kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5f3de-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="5f3de-111">Dokładne wersja kompilatora używane i jego zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="5f3de-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="5f3de-112">Ścieżka bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5f3de-112">The current directory path.</span></span>
- <span data-ttu-id="5f3de-113">Wszystkie pliki binarne treści jawnie przekazany do kompilatora bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="5f3de-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
    - <span data-ttu-id="5f3de-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="5f3de-114">Source files</span></span>
    - <span data-ttu-id="5f3de-115">przywoływanych zestawach</span><span class="sxs-lookup"><span data-stu-id="5f3de-115">Referenced assemblies</span></span>
    - <span data-ttu-id="5f3de-116">Przywoływany modułów</span><span class="sxs-lookup"><span data-stu-id="5f3de-116">Referenced modules</span></span>
    - <span data-ttu-id="5f3de-117">Zasoby</span><span class="sxs-lookup"><span data-stu-id="5f3de-117">Resources</span></span>
    - <span data-ttu-id="5f3de-118">Plik klucza silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="5f3de-118">The strong name key file</span></span>
    - <span data-ttu-id="5f3de-119">@ pliki odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="5f3de-119">@ response files</span></span>
    - <span data-ttu-id="5f3de-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="5f3de-120">Analyzers</span></span>
    - <span data-ttu-id="5f3de-121">Zestawy reguł</span><span class="sxs-lookup"><span data-stu-id="5f3de-121">Rulesets</span></span>
    - <span data-ttu-id="5f3de-122">Dodatkowe pliki, które mogą być używane przez analizatory</span><span class="sxs-lookup"><span data-stu-id="5f3de-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="5f3de-123">Bieżąca kultura (język, w którym diagnostyki i wyjątków są produkowane wiadomości).</span><span class="sxs-lookup"><span data-stu-id="5f3de-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="5f3de-124">Domyślnym kodowaniem (lub bieżącej stronie kodowej) Jeśli nie określono kodowanie.</span><span class="sxs-lookup"><span data-stu-id="5f3de-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="5f3de-125">Istnienie, brak i zawartość plików w ścieżkach wyszukiwania przez kompilator (określonej, na przykład przez `/lib` lub `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="5f3de-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="5f3de-126">Platforma CLR, na którym jest wykonywane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="5f3de-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="5f3de-127">Wartość `%LIBPATH%`, co może wpłynąć na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="5f3de-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="5f3de-128">Gdy publicznie dostępnych źródeł, kompilacji deterministycznej może służyć do ustalenia, czy dane binarne ma być kompilowana z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="5f3de-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="5f3de-129">Może być również przydatne w systemie kompilacji ciągłej do określenia, czy konieczne można wykonać kroki procesu kompilacji, które są zależne od zmian w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="5f3de-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="5f3de-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f3de-130">See Also</span></span>  
 [<span data-ttu-id="5f3de-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5f3de-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="5f3de-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5f3de-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
