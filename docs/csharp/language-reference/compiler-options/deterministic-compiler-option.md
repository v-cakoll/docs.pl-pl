---
title: -deterministycznyC# (opcje kompilatora)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455187"
---
# <a name="-deterministic"></a><span data-ttu-id="41b1f-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="41b1f-102">-deterministic</span></span>

<span data-ttu-id="41b1f-103">Powoduje, że kompilator tworzy zestaw, którego bajty w bajtach są identyczne w kompilacjach dla identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="41b1f-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="41b1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b1f-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="41b1f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41b1f-105">Remarks</span></span>

<span data-ttu-id="41b1f-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych są unikatowe, ponieważ kompilator dodaje sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="41b1f-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="41b1f-107">Opcja `-deterministic` służy do tworzenia *deterministycznego zestawu*, który jest identyczny z zawartością binarną w kompilacjach, o ile dane wejściowe pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="41b1f-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="41b1f-108">Kompilator traktuje następujące dane wejściowe na potrzeby ustalenia:</span><span class="sxs-lookup"><span data-stu-id="41b1f-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="41b1f-109">Sekwencja parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="41b1f-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="41b1f-110">Zawartość pliku odpowiedzi kompilatora. rsp.</span><span class="sxs-lookup"><span data-stu-id="41b1f-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="41b1f-111">Dokładna wersja używanego kompilatora oraz zestawy, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="41b1f-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="41b1f-112">Bieżąca ścieżka katalogu.</span><span class="sxs-lookup"><span data-stu-id="41b1f-112">The current directory path.</span></span>
- <span data-ttu-id="41b1f-113">Zawartość binarna wszystkich plików jawnie przekazana do kompilatora bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="41b1f-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="41b1f-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="41b1f-114">Source files</span></span>
  - <span data-ttu-id="41b1f-115">Przywoływane zestawy</span><span class="sxs-lookup"><span data-stu-id="41b1f-115">Referenced assemblies</span></span>
  - <span data-ttu-id="41b1f-116">Moduły, do których istnieją odwołania</span><span class="sxs-lookup"><span data-stu-id="41b1f-116">Referenced modules</span></span>
  - <span data-ttu-id="41b1f-117">Resources</span><span class="sxs-lookup"><span data-stu-id="41b1f-117">Resources</span></span>
  - <span data-ttu-id="41b1f-118">Plik klucza o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="41b1f-118">The strong name key file</span></span>
  - <span data-ttu-id="41b1f-119">pliki odpowiedzi @</span><span class="sxs-lookup"><span data-stu-id="41b1f-119">@ response files</span></span>
  - <span data-ttu-id="41b1f-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="41b1f-120">Analyzers</span></span>
  - <span data-ttu-id="41b1f-121">Zestaw reguł</span><span class="sxs-lookup"><span data-stu-id="41b1f-121">Rulesets</span></span>
  - <span data-ttu-id="41b1f-122">Dodatkowe pliki, które mogą być używane przez analizatory</span><span class="sxs-lookup"><span data-stu-id="41b1f-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="41b1f-123">Bieżąca kultura (dla języka, w którym są generowane diagnostyczne i komunikaty o wyjątkach).</span><span class="sxs-lookup"><span data-stu-id="41b1f-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="41b1f-124">Domyślne kodowanie (lub bieżącą stronę kodową), Jeśli kodowanie nie jest określone.</span><span class="sxs-lookup"><span data-stu-id="41b1f-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="41b1f-125">Istnienie, nieistnienie i zawartość plików na ścieżkach wyszukiwania kompilatora (na przykład przez `-lib` lub `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="41b1f-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="41b1f-126">Platforma CLR, na której jest uruchomiony kompilator.</span><span class="sxs-lookup"><span data-stu-id="41b1f-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="41b1f-127">Wartość `%LIBPATH%`, która może wpływać na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="41b1f-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="41b1f-128">Gdy źródła są dostępne publicznie, można użyć deterministycznej kompilacji do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="41b1f-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="41b1f-129">Może być również przydatna w systemie ciągłej kompilacji, aby określić, czy należy wykonać kroki kompilacji, które są zależne od zmian w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="41b1f-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="41b1f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b1f-130">See also</span></span>

- [<span data-ttu-id="41b1f-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="41b1f-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="41b1f-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="41b1f-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
