---
title: Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#
description: Wprowadzenie nowych funkcji języków w bibliotece może mieć wpływ na kod, który go używa.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399386"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="9083f-103">Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#</span><span class="sxs-lookup"><span data-stu-id="9083f-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="9083f-104">Zgodność jest bardzo ważnym celem, ponieważ nowe funkcje są dodawane do języka C#.</span><span class="sxs-lookup"><span data-stu-id="9083f-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="9083f-105">W prawie wszystkich przypadkach istniejący kod można ponownie skompilować z nową wersją kompilatora bez żadnego problemu.</span><span class="sxs-lookup"><span data-stu-id="9083f-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="9083f-106">Podczas przyjmowania nowych funkcji języka w bibliotece może być wymagana większa ostrożność.</span><span class="sxs-lookup"><span data-stu-id="9083f-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="9083f-107">Być może tworzysz nową bibliotekę z funkcjami znalezionymi w najnowszej wersji i musisz upewnić się, że aplikacje utworzone przy użyciu poprzednich wersji kompilatora mogą z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="9083f-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="9083f-108">Możesz też uaktualnić istniejącą bibliotekę, a wielu użytkowników może nie mieć jeszcze uaktualnionych wersji.</span><span class="sxs-lookup"><span data-stu-id="9083f-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="9083f-109">Podejmując decyzje dotyczące przyjmowania nowych funkcji, musisz wziąć pod uwagę dwie odmiany zgodności: kompatybilność ze źródłem i zgodna z plikami binarnymi.</span><span class="sxs-lookup"><span data-stu-id="9083f-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="9083f-110">Zmiany zgodne z binarnymi</span><span class="sxs-lookup"><span data-stu-id="9083f-110">Binary compatible changes</span></span>

<span data-ttu-id="9083f-111">Zmiany w bibliotece są **zgodne z plikami binarnymi,** gdy zaktualizowana biblioteka może być używana bez odbudowy aplikacji i bibliotek, które jej używają.</span><span class="sxs-lookup"><span data-stu-id="9083f-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="9083f-112">Zestawy zależne nie są wymagane do przebudowy, ani nie są wymagane żadne zmiany kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9083f-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="9083f-113">Zmiany zgodne z binarnymi są również źródłem zmian zgodnych.</span><span class="sxs-lookup"><span data-stu-id="9083f-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="9083f-114">Zmiany zgodne ze źródłem</span><span class="sxs-lookup"><span data-stu-id="9083f-114">Source compatible changes</span></span>

<span data-ttu-id="9083f-115">Zmiany w bibliotece są **zgodne ze źródłem,** gdy aplikacje i biblioteki korzystające z biblioteki nie wymagają zmian kodu źródłowego, ale źródło musi zostać ponownie skompilowane względem nowej wersji, aby działała poprawnie.</span><span class="sxs-lookup"><span data-stu-id="9083f-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="9083f-116">Niekompatybilne zmiany</span><span class="sxs-lookup"><span data-stu-id="9083f-116">Incompatible changes</span></span>

<span data-ttu-id="9083f-117">Jeśli zmiana nie jest **zgodna ze źródłem** ani **zgodnym z plikami binarnymi,** zmiany kodu źródłowego wraz z ponowną kompilacją są wymagane w bibliotekach zależnych i aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="9083f-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="9083f-118">Ocena biblioteki</span><span class="sxs-lookup"><span data-stu-id="9083f-118">Evaluate your library</span></span>

<span data-ttu-id="9083f-119">Te pojęcia zgodności wpływają na publiczne i chronione deklaracje dla biblioteki, a nie jej implementacji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="9083f-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="9083f-120">Przyjęcie jakichkolwiek nowych funkcji wewnętrznie są zawsze **binarne kompatybilne**.</span><span class="sxs-lookup"><span data-stu-id="9083f-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="9083f-121">Zmiany **zgodne z plikami binarnymi** zapewniają nową składnię, która generuje ten sam skompilowany kod dla deklaracji publicznych, co starsza składnia.</span><span class="sxs-lookup"><span data-stu-id="9083f-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="9083f-122">Na przykład zmiana metody na element członkowski zabudowany wyrażenie jest zmiana **zgodna z binarnymi:**</span><span class="sxs-lookup"><span data-stu-id="9083f-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="9083f-123">Oryginalny kod:</span><span class="sxs-lookup"><span data-stu-id="9083f-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="9083f-124">Nowy kod:</span><span class="sxs-lookup"><span data-stu-id="9083f-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="9083f-125">**Zmiany zgodne ze źródłem** wprowadzają składnię, która zmienia skompilowany kod dla publicznego elementu członkowskiego, ale w sposób zgodny z istniejącymi witrynami wywołań.</span><span class="sxs-lookup"><span data-stu-id="9083f-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="9083f-126">Na przykład zmiana podpisu metody z parametru według wartości na `in` parametr odniesienia jest zgodna ze źródłem, ale nie zgodna z plikami binarnymi:</span><span class="sxs-lookup"><span data-stu-id="9083f-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="9083f-127">Oryginalny kod:</span><span class="sxs-lookup"><span data-stu-id="9083f-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="9083f-128">Nowy kod:</span><span class="sxs-lookup"><span data-stu-id="9083f-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="9083f-129">[Co nowego](index.md) artykułu zanotować, jeśli wprowadzenie funkcji, która wpływa na deklaracje publiczne jest zgodne ze źródłem lub binarne zgodne.</span><span class="sxs-lookup"><span data-stu-id="9083f-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
