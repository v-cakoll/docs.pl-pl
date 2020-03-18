---
title: -deterministyczne (Opcje kompilatora C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455187"
---
# <a name="-deterministic"></a><span data-ttu-id="13c62-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="13c62-102">-deterministic</span></span>

<span data-ttu-id="13c62-103">Powoduje, że kompilator do produkcji zestawu, którego dane wyjściowe bajt dla bajtów jest identyczny w kompilacjach dla identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="13c62-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="13c62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c62-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="13c62-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c62-105">Remarks</span></span>

<span data-ttu-id="13c62-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator dodaje sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="13c62-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="13c62-107">Opcja ta `-deterministic` służy do tworzenia *zestawu deterministycznego,* którego zawartość binarna jest identyczna w kompilacjach, o ile dane wejściowe pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="13c62-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="13c62-108">Kompilator uwzględnia następujące dane wejściowe w celu determinizmu:</span><span class="sxs-lookup"><span data-stu-id="13c62-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="13c62-109">Sekwencja parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="13c62-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="13c62-110">Zawartość pliku odpowiedzi .rsp kompilatora.</span><span class="sxs-lookup"><span data-stu-id="13c62-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="13c62-111">Dokładna wersja kompilatora używane i jego zestawy odwołuje.</span><span class="sxs-lookup"><span data-stu-id="13c62-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="13c62-112">Bieżąca ścieżka katalogu.</span><span class="sxs-lookup"><span data-stu-id="13c62-112">The current directory path.</span></span>
- <span data-ttu-id="13c62-113">Zawartość binarna wszystkich plików jawnie przekazywane do kompilatora bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="13c62-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="13c62-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="13c62-114">Source files</span></span>
  - <span data-ttu-id="13c62-115">Zestawy odniesienia</span><span class="sxs-lookup"><span data-stu-id="13c62-115">Referenced assemblies</span></span>
  - <span data-ttu-id="13c62-116">Moduły referencyjne</span><span class="sxs-lookup"><span data-stu-id="13c62-116">Referenced modules</span></span>
  - <span data-ttu-id="13c62-117">Zasoby</span><span class="sxs-lookup"><span data-stu-id="13c62-117">Resources</span></span>
  - <span data-ttu-id="13c62-118">Plik klucza silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="13c62-118">The strong name key file</span></span>
  - <span data-ttu-id="13c62-119">@ pliki odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="13c62-119">@ response files</span></span>
  - <span data-ttu-id="13c62-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="13c62-120">Analyzers</span></span>
  - <span data-ttu-id="13c62-121">Zasady</span><span class="sxs-lookup"><span data-stu-id="13c62-121">Rulesets</span></span>
  - <span data-ttu-id="13c62-122">Dodatkowe pliki, które mogą być używane przez analizatory</span><span class="sxs-lookup"><span data-stu-id="13c62-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="13c62-123">Bieżąca kultura (dla języka, w którym są tworzone komunikaty diagnostyczne i wyjątki).</span><span class="sxs-lookup"><span data-stu-id="13c62-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="13c62-124">Domyślne kodowanie (lub bieżąca strona kodowa), jeśli kodowanie nie jest określone.</span><span class="sxs-lookup"><span data-stu-id="13c62-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="13c62-125">Istnienie, nieistnienie i zawartość plików na ścieżkach wyszukiwania kompilatora (określone `-lib` na `-recurse`przykład przez lub ).</span><span class="sxs-lookup"><span data-stu-id="13c62-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="13c62-126">Platforma CLR, na której jest uruchamiany kompilator.</span><span class="sxs-lookup"><span data-stu-id="13c62-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="13c62-127">Wartość `%LIBPATH%`, które mogą mieć wpływ na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="13c62-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="13c62-128">Gdy źródła są publicznie dostępne, kompilacji deterministycznej może służyć do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="13c62-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="13c62-129">Może być również przydatne w systemie ciągłej kompilacji do określania, czy kroki kompilacji, które są zależne od zmian do binarnego muszą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="13c62-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="13c62-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c62-130">See also</span></span>

- [<span data-ttu-id="13c62-131">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="13c62-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="13c62-132">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="13c62-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
