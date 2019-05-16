---
title: Wersja i zaktualizuj uwagi dla deweloperów języka C#
description: Wprowadzenie do nowych funkcji języków w bibliotece może wpłynąć na kod, który korzysta z niego.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634489"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="0ae06-103">Wersja i zaktualizuj uwagi dla deweloperów języka C#</span><span class="sxs-lookup"><span data-stu-id="0ae06-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="0ae06-104">Zgodność jest bardzo ważne cel w miarę dodawania nowych funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="0ae06-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="0ae06-105">Prawie we wszystkich przypadkach istniejący kod może ponownie kompilowana do nowej wersji kompilatora bez żadnych problemu.</span><span class="sxs-lookup"><span data-stu-id="0ae06-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="0ae06-106">Ostrożnie mogą być wymagane, gdy przyjmują nowe funkcje języka w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="0ae06-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="0ae06-107">Jego przy użyciu funkcji, które znajdują się w najnowszej wersji tworzy nową bibliotekę i należy do zagwarantowania, że aplikacje utworzone przy użyciu poprzedniej wersji kompilatora może być użyty.</span><span class="sxs-lookup"><span data-stu-id="0ae06-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="0ae06-108">Lub może być uaktualniania istniejącej biblioteki i wielu użytkowników może nie uaktualniono wersje jeszcze.</span><span class="sxs-lookup"><span data-stu-id="0ae06-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="0ae06-109">Przy podejmowaniu decyzji o przyjęcie nowych funkcji, należy wziąć pod uwagę dwie odmiany zgodność: źródłowy zgodny i zgodne dane binarne.</span><span class="sxs-lookup"><span data-stu-id="0ae06-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="0ae06-110">Binarny zmiany zgodne</span><span class="sxs-lookup"><span data-stu-id="0ae06-110">Binary compatible changes</span></span>

<span data-ttu-id="0ae06-111">Zmiany w bibliotece są **zgodne dane binarne** gdy zaktualizowano biblioteki mogą być używane w taki sposób, bez ponowne tworzenie aplikacji i bibliotek, które go używają.</span><span class="sxs-lookup"><span data-stu-id="0ae06-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="0ae06-112">Zależne zestawy nie są wymagane do można odbudować ani nie są wymagane zmiany kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0ae06-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="0ae06-113">Binarny zgodne nie są zgodne zmiany źródła.</span><span class="sxs-lookup"><span data-stu-id="0ae06-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="0ae06-114">Zmiany zgodne źródło</span><span class="sxs-lookup"><span data-stu-id="0ae06-114">Source compatible changes</span></span>

<span data-ttu-id="0ae06-115">Zmiany w bibliotece są **zgodne źródło** po aplikacji i bibliotek, korzystających z biblioteki nie wymagają zmiany kodu źródłowego, ale źródło powodującej względem nowej wersji, aby działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="0ae06-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="0ae06-116">Niezgodne zmiany</span><span class="sxs-lookup"><span data-stu-id="0ae06-116">Incompatible changes</span></span>

<span data-ttu-id="0ae06-117">Jeśli zmiany nie jest ani **zgodne źródło** ani **zgodne dane binarne**, zmiany kodu źródłowego oraz ponownej kompilacji są wymagane w aplikacjach i zależne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0ae06-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="0ae06-118">Oceń biblioteki</span><span class="sxs-lookup"><span data-stu-id="0ae06-118">Evaluate your library</span></span>

<span data-ttu-id="0ae06-119">Te pojęcia zgodności wpływają na deklaracje publiczne i chronione, biblioteki, a nie wewnętrzną implementację.</span><span class="sxs-lookup"><span data-stu-id="0ae06-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="0ae06-120">Wewnętrznie przyjęcie żadnych nowych funkcji są zawsze **zgodne dane binarne**.</span><span class="sxs-lookup"><span data-stu-id="0ae06-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="0ae06-121">**Binarny zgodnego** zmiany Podaj nową składnię, która generuje ten sam kod skompilowany dla deklaracji na publiczny jako starsza składnia.</span><span class="sxs-lookup"><span data-stu-id="0ae06-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="0ae06-122">Na przykład zmiana metody do elementu członkowskiego z wyrażeniem w treści jest **zgodne dane binarne** zmiany:</span><span class="sxs-lookup"><span data-stu-id="0ae06-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="0ae06-123">Oryginalny kod:</span><span class="sxs-lookup"><span data-stu-id="0ae06-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="0ae06-124">Nowy kod:</span><span class="sxs-lookup"><span data-stu-id="0ae06-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="0ae06-125">**Zgodne źródło** zmiany wprowadzają składnia, która zmienia kod skompilowany członka publicznego, ale w sposób zgodny z istniejących witryn wywołania.</span><span class="sxs-lookup"><span data-stu-id="0ae06-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="0ae06-126">Na przykład zmiana sygnatury metody z przez wartość parametru, aby `in` przez odwołanie parametr jest zgodne, źródła, ale nie binarne zgodnych:</span><span class="sxs-lookup"><span data-stu-id="0ae06-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="0ae06-127">Oryginalny kod:</span><span class="sxs-lookup"><span data-stu-id="0ae06-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="0ae06-128">Nowy kod:</span><span class="sxs-lookup"><span data-stu-id="0ae06-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="0ae06-129">[What's new](index.md) artykułów należy pamiętać, jeśli wprowadzenie do funkcji, który wpływa na publicznego deklaracje zgodnego źródła lub zgodne dane binarne.</span><span class="sxs-lookup"><span data-stu-id="0ae06-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
