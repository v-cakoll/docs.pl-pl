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
ms.openlocfilehash: 9f9aca20a3ff65d061c04a21e31db3fb5eab62ba
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099220"
---
# <a name="-deterministic"></a><span data-ttu-id="7136c-102">-deterministyczne</span><span class="sxs-lookup"><span data-stu-id="7136c-102">-deterministic</span></span>

<span data-ttu-id="7136c-103">Powoduje, że kompilator generuje zestawu, którego dane wyjściowe dla bajt jest identyczna w kompilacjach identycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7136c-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="7136c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7136c-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="7136c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7136c-105">Remarks</span></span>

<span data-ttu-id="7136c-106">Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator sam doda sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczby losowe.</span><span class="sxs-lookup"><span data-stu-id="7136c-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="7136c-107">Możesz użyć `-deterministic` opcję, aby wygenerować *deterministyczne zestawu*, jedną z którego zawartość binarna jest identyczne w kompilacji, tak długo, jak dane wejściowe pozostają bez zmian.</span><span class="sxs-lookup"><span data-stu-id="7136c-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="7136c-108">Kompilator traktuje następujące dane wejściowe na potrzeby determinizm:</span><span class="sxs-lookup"><span data-stu-id="7136c-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="7136c-109">Sekwencja parametry wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7136c-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="7136c-110">Zawartość pliku odpowiedzi rsp kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7136c-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="7136c-111">Dokładne wersję kompilatora, używane, a jego przywoływanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="7136c-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="7136c-112">Ścieżka bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7136c-112">The current directory path.</span></span>
- <span data-ttu-id="7136c-113">Binarny zawartość wszystkich plików jawnie przekazywane do kompilator bezpośrednio lub pośrednio, w tym:</span><span class="sxs-lookup"><span data-stu-id="7136c-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
    - <span data-ttu-id="7136c-114">Pliki źródłowe</span><span class="sxs-lookup"><span data-stu-id="7136c-114">Source files</span></span>
    - <span data-ttu-id="7136c-115">przywoływanych zestawach</span><span class="sxs-lookup"><span data-stu-id="7136c-115">Referenced assemblies</span></span>
    - <span data-ttu-id="7136c-116">Moduły odwołania</span><span class="sxs-lookup"><span data-stu-id="7136c-116">Referenced modules</span></span>
    - <span data-ttu-id="7136c-117">Resources</span><span class="sxs-lookup"><span data-stu-id="7136c-117">Resources</span></span>
    - <span data-ttu-id="7136c-118">Plik klucza silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="7136c-118">The strong name key file</span></span>
    - <span data-ttu-id="7136c-119">@ pliki odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="7136c-119">@ response files</span></span>
    - <span data-ttu-id="7136c-120">Analizatory</span><span class="sxs-lookup"><span data-stu-id="7136c-120">Analyzers</span></span>
    - <span data-ttu-id="7136c-121">Zestawy reguł</span><span class="sxs-lookup"><span data-stu-id="7136c-121">Rulesets</span></span>
    - <span data-ttu-id="7136c-122">Dodatkowe pliki, które mogą być używane przez analizatorów</span><span class="sxs-lookup"><span data-stu-id="7136c-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="7136c-123">Bieżącą kulturą (język, w których dane diagnostyczne i wyjątków są produkowane wiadomości).</span><span class="sxs-lookup"><span data-stu-id="7136c-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="7136c-124">Domyślnym kodowaniem (lub bieżącej stronie kodowej) Jeśli nie określono kodowanie.</span><span class="sxs-lookup"><span data-stu-id="7136c-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="7136c-125">Istnienie, nie istnieje i zawartość plików na ścieżki wyszukiwania kompilatora (określone, na przykład przez `/lib` lub `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="7136c-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="7136c-126">Platforma CLR, na którym jest uruchamiany kompilator.</span><span class="sxs-lookup"><span data-stu-id="7136c-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="7136c-127">Wartość `%LIBPATH%`, co może wpłynąć na ładowanie zależności analizatora.</span><span class="sxs-lookup"><span data-stu-id="7136c-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="7136c-128">W przypadku publicznie dostępnego źródła kompilacji deterministycznej może służyć do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="7136c-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="7136c-129">Również może być przydatne w systemie kompilacji ciągłej do określenia, czy należy wykonać kroki kompilacji, które są zależne od zmian w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="7136c-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="7136c-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7136c-130">See Also</span></span>  

- [<span data-ttu-id="7136c-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7136c-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="7136c-132">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7136c-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
