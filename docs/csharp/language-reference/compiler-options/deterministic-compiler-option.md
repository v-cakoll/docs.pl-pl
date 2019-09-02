---
title: -deterministycznyC# (opcje kompilatora)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202922"
---
# <a name="-deterministic"></a><span data-ttu-id="fbac9-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="fbac9-102">-deterministic</span></span>

<span data-ttu-id="fbac9-103">Powoduje, że kompilator tworzy zestaw, którego bajty w bajtach są identyczne w kompilacjach dla identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="fbac9-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbac9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbac9-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="fbac9-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbac9-105">Remarks</span></span>

<span data-ttu-id="fbac9-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych są unikatowe, ponieważ kompilator dodaje sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="fbac9-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="fbac9-107">Używasz opcji do tworzenia deterministycznego zestawu, który jest identyczny z zawartością binarną w kompilacjach, tak długo, jak dane wejściowe pozostają takie same. `-deterministic`</span><span class="sxs-lookup"><span data-stu-id="fbac9-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="fbac9-108">Kompilator traktuje następujące dane wejściowe na potrzeby ustalenia:</span><span class="sxs-lookup"><span data-stu-id="fbac9-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="fbac9-109">Sekwencja parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fbac9-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="fbac9-110">Zawartość pliku odpowiedzi kompilatora. rsp.</span><span class="sxs-lookup"><span data-stu-id="fbac9-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="fbac9-111">Dokładna wersja używanego kompilatora oraz zestawy, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="fbac9-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="fbac9-112">Bieżąca ścieżka katalogu.</span><span class="sxs-lookup"><span data-stu-id="fbac9-112">The current directory path.</span></span>
- <span data-ttu-id="fbac9-113">Zawartość binarna wszystkich plików jawnie przekazana do kompilatora bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="fbac9-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="fbac9-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="fbac9-114">Source files</span></span>
  - <span data-ttu-id="fbac9-115">Przywoływane zestawy</span><span class="sxs-lookup"><span data-stu-id="fbac9-115">Referenced assemblies</span></span>
  - <span data-ttu-id="fbac9-116">Moduły, do których istnieją odwołania</span><span class="sxs-lookup"><span data-stu-id="fbac9-116">Referenced modules</span></span>
  - <span data-ttu-id="fbac9-117">Zasoby</span><span class="sxs-lookup"><span data-stu-id="fbac9-117">Resources</span></span>
  - <span data-ttu-id="fbac9-118">Plik klucza o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="fbac9-118">The strong name key file</span></span>
  - <span data-ttu-id="fbac9-119">pliki odpowiedzi @</span><span class="sxs-lookup"><span data-stu-id="fbac9-119">@ response files</span></span>
  - <span data-ttu-id="fbac9-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="fbac9-120">Analyzers</span></span>
  - <span data-ttu-id="fbac9-121">Zestaw reguł</span><span class="sxs-lookup"><span data-stu-id="fbac9-121">Rulesets</span></span>
  - <span data-ttu-id="fbac9-122">Dodatkowe pliki, które mogą być używane przez analizatory</span><span class="sxs-lookup"><span data-stu-id="fbac9-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="fbac9-123">Bieżąca kultura (dla języka, w którym są generowane diagnostyczne i komunikaty o wyjątkach).</span><span class="sxs-lookup"><span data-stu-id="fbac9-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="fbac9-124">Domyślne kodowanie (lub bieżącą stronę kodową), Jeśli kodowanie nie jest określone.</span><span class="sxs-lookup"><span data-stu-id="fbac9-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="fbac9-125">Istnienie, nieistnienie i zawartość plików na ścieżkach wyszukiwania kompilatora (na przykład przez `/lib` lub `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="fbac9-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="fbac9-126">Platforma CLR, na której jest uruchomiony kompilator.</span><span class="sxs-lookup"><span data-stu-id="fbac9-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="fbac9-127">Wartość `%LIBPATH%`, która może wpływać na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="fbac9-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="fbac9-128">Gdy źródła są dostępne publicznie, można użyć deterministycznej kompilacji do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="fbac9-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="fbac9-129">Może być również przydatna w systemie ciągłej kompilacji, aby określić, czy należy wykonać kroki kompilacji, które są zależne od zmian w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="fbac9-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbac9-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbac9-130">See also</span></span>

- [<span data-ttu-id="fbac9-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="fbac9-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fbac9-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fbac9-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
