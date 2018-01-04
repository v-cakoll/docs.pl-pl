---
title: moduloObjectHashcode MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 618196473e8e947e84b0506771bce84ee71a1c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="b419f-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="b419f-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="b419f-103">`moduloObjectHashcode` Zarządzany Asystent debugowania (MDA) zmiany zachowania <xref:System.Object> klasy do wykonania modulo operacja skrótu zwrócony przez <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b419f-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="b419f-104">Modulo domyślnego dla tego MDA wynosi 1, co powoduje, że <xref:System.Object.GetHashCode%2A> do zwrócenia 0 dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="b419f-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b419f-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="b419f-105">Symptoms</span></span>  
 <span data-ttu-id="b419f-106">Po przeniesieniu do nowej wersji środowisko uruchomieniowe języka wspólnego (CLR), program nie działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="b419f-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="b419f-107">Program otrzymuje z niewłaściwym obiektem <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="b419f-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="b419f-108">Kolejność wyliczenie z <xref:System.Collections.Hashtable> zawiera zmiany, która dzieli program.</span><span class="sxs-lookup"><span data-stu-id="b419f-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="b419f-109">Dwa obiekty używane równe nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="b419f-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="b419f-110">Dwa obiekty używane różnej teraz są takie same.</span><span class="sxs-lookup"><span data-stu-id="b419f-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b419f-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b419f-111">Cause</span></span>  
 <span data-ttu-id="b419f-112">Program może występować z niewłaściwym obiektem <xref:System.Collections.Hashtable> ponieważ wykonania <xref:System.Object.Equals%2A> metody w klasie klucza do <xref:System.Collections.Hashtable> testy równości obiektów przez porównanie wyników wywołanie <xref:System.Object.GetHashCode%2A> — metoda .</span><span class="sxs-lookup"><span data-stu-id="b419f-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="b419f-113">Skrótu nie powinien służyć do testowania równość obiektu, ponieważ dwa obiekty może mieć taki sam skrót, nawet jeśli ich odpowiednich pól mają różne wartości.</span><span class="sxs-lookup"><span data-stu-id="b419f-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="b419f-114">Te kolizji kod skrótu, wystąpić sporadycznych w praktyce.</span><span class="sxs-lookup"><span data-stu-id="b419f-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="b419f-115">Wpływ ma na <xref:System.Collections.Hashtable> wyszukiwanie jest równe wyświetlane są dwa klucze, które nie są takie same, czy nieprawidłowy obiekt jest zwracany z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="b419f-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="b419f-116">Ze względu na wydajność, implementacja <xref:System.Object.GetHashCode%2A> można przełączać się między wersji środowiska uruchomieniowego, więc konflikty, które nie mogą wystąpić w jednej wersji może wystąpić w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="b419f-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="b419f-117">Włącz to zdarzenie MDA sprawdzić, czy używany kod ma usterki podczas kolizji skrótu.</span><span class="sxs-lookup"><span data-stu-id="b419f-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="b419f-118">Włączenie tej opcji, to zdarzenie MDA powoduje, że <xref:System.Object.GetHashCode%2A> metoda zwraca 0, co kolizji wszystkie kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="b419f-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="b419f-119">Tylko efekt Włączanie przez to zdarzenie MDA powinny mieć programu jest wolniej uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="b419f-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="b419f-120">Kolejność wyliczenie z <xref:System.Collections.Hashtable> może zmienić z jednej wersji środowiska uruchomieniowego, jeśli inny algorytm używany do obliczania skrótu dla zmian klucza.</span><span class="sxs-lookup"><span data-stu-id="b419f-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="b419f-121">Aby sprawdzić, czy program trwało zależności rzędu wyliczenie kluczy lub wartości spoza tablicy skrótów, można włączyć to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="b419f-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b419f-122">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b419f-122">Resolution</span></span>  
 <span data-ttu-id="b419f-123">Nigdy nie używaj skrótu zastępuje tożsamość obiektu.</span><span class="sxs-lookup"><span data-stu-id="b419f-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="b419f-124">Implementowanie zastąpienie z <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody do porównania nie skrótu.</span><span class="sxs-lookup"><span data-stu-id="b419f-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="b419f-125">Nie należy tworzyć zależności rzędu wyliczenia kluczy lub wartości w tabelach skrótów.</span><span class="sxs-lookup"><span data-stu-id="b419f-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b419f-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b419f-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="b419f-127">Aplikacje działać wolniej, gdy to zdarzenie MDA jest włączona.</span><span class="sxs-lookup"><span data-stu-id="b419f-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="b419f-128">To zdarzenie MDA po prostu przyjmuje wartość skrótu, które mogłyby być zwracane i zamiast tego zwraca resztę po podzielona przez moduł.</span><span class="sxs-lookup"><span data-stu-id="b419f-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b419f-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b419f-129">Output</span></span>  
 <span data-ttu-id="b419f-130">Nie ma żadnych danych wyjściowych dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="b419f-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b419f-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b419f-131">Configuration</span></span>  
 <span data-ttu-id="b419f-132">`modulus` Atrybut określa modulo używane na wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="b419f-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="b419f-133">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="b419f-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b419f-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b419f-134">See Also</span></span>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b419f-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b419f-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
