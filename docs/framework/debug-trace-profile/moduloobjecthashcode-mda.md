---
title: moduloObjectHashcode MDA
description: Przejrzyj moduloObjectHashcode Managed Debug Assistant (MDA), co powoduje zmianę klasy obiektu w celu uzyskania wartości pozostałej w wyniku metody GetHashCode.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052068"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="c7806-103">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="c7806-103">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="c7806-104">`moduloObjectHashcode`Asystent debugowania zarządzanego (MDA) zmienia zachowanie <xref:System.Object> klasy w celu wykonania operacji modulo dla kodu skrótu zwracanego przez <xref:System.Object.GetHashCode%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="c7806-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c7806-105">Domyślny moduł dla tego elementu MDA wynosi 1, co powoduje <xref:System.Object.GetHashCode%2A> zwrócenie wartości 0 dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="c7806-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c7806-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="c7806-106">Symptoms</span></span>  
 <span data-ttu-id="c7806-107">Po przejściu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR) program nie jest już wykonywany prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="c7806-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="c7806-108">Program pobiera nieprawidłowy obiekt z <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="c7806-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="c7806-109">Kolejność wyliczania z elementu a <xref:System.Collections.Hashtable> ma zmianę, która powoduje przerwanie działania programu.</span><span class="sxs-lookup"><span data-stu-id="c7806-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="c7806-110">Dwa obiekty, które były takie same, nie są już równe.</span><span class="sxs-lookup"><span data-stu-id="c7806-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="c7806-111">Dwa obiekty, które nie są równe, są teraz równe.</span><span class="sxs-lookup"><span data-stu-id="c7806-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c7806-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c7806-112">Cause</span></span>  
 <span data-ttu-id="c7806-113">Program może uzyskać niewłaściwy obiekt z, <xref:System.Collections.Hashtable> ponieważ implementacja <xref:System.Object.Equals%2A> metody na klasie klucza w celu <xref:System.Collections.Hashtable> sprawdzenia równości obiektów, porównując wyniki wywołania <xref:System.Object.GetHashCode%2A> metody...</span><span class="sxs-lookup"><span data-stu-id="c7806-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c7806-114">Kodów skrótów nie należy używać do testowania równości obiektów, ponieważ dwa obiekty mogą mieć ten sam kod skrótu, nawet jeśli odpowiadające im pola mają różne wartości.</span><span class="sxs-lookup"><span data-stu-id="c7806-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="c7806-115">Te konflikty kodu mieszania, chociaż rzadko występują, są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="c7806-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="c7806-116">Efekt na <xref:System.Collections.Hashtable> wyszukiwaniu polega na tym, że dwa klucze, które nie są równe, są równe, a niewłaściwy obiekt jest zwracany z <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="c7806-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="c7806-117">Ze względu na wydajność implementacja programu <xref:System.Object.GetHashCode%2A> może się zmieniać między wersjami środowiska uruchomieniowego, więc kolizje, które mogą nie wystąpić w jednej wersji, mogą wystąpić w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="c7806-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="c7806-118">Włącz tę funkcję MDA, aby sprawdzić, czy kod ma błędy w przypadku kolizji kodów mieszania.</span><span class="sxs-lookup"><span data-stu-id="c7806-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="c7806-119">Po włączeniu tego MDA powoduje, że <xref:System.Object.GetHashCode%2A> Metoda zwraca wartość 0, co koliduje ze wszystkimi kodami mieszania.</span><span class="sxs-lookup"><span data-stu-id="c7806-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="c7806-120">Jedynym efektem włączenia tego pakietu w programie jest to, że program działa wolniej.</span><span class="sxs-lookup"><span data-stu-id="c7806-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="c7806-121">Kolejność wyliczania z programu <xref:System.Collections.Hashtable> może ulec zmianie z jednej wersji środowiska uruchomieniowego na inną, jeśli algorytm używany do obliczania kodów skrótów dla zmiany klucza.</span><span class="sxs-lookup"><span data-stu-id="c7806-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="c7806-122">Aby sprawdzić, czy program pobrał zależność od kolejności wyliczania kluczy lub wartości z tabeli skrótów, można włączyć to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="c7806-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c7806-123">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c7806-123">Resolution</span></span>  
 <span data-ttu-id="c7806-124">Nigdy nie używaj kodów skrótu jako substytutu dla tożsamości obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7806-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="c7806-125">Zaimplementuj przesłonięcie <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody, aby nie porównywać kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="c7806-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="c7806-126">Nie należy tworzyć zależności względem kolejności wyliczeń kluczy lub wartości w tabelach skrótów.</span><span class="sxs-lookup"><span data-stu-id="c7806-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7806-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c7806-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7806-128">Aplikacje działają wolniej, gdy to MDA jest włączone.</span><span class="sxs-lookup"><span data-stu-id="c7806-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="c7806-129">To zdarzenie MDA po prostu pobiera zwrócony kod skrótu, a zamiast tego zwraca resztę przy poddzieleniu przez moduł.</span><span class="sxs-lookup"><span data-stu-id="c7806-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7806-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c7806-130">Output</span></span>  
 <span data-ttu-id="c7806-131">Brak danych wyjściowych dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="c7806-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c7806-132">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="c7806-132">Configuration</span></span>  
 <span data-ttu-id="c7806-133">Ten `modulus` atrybut określa moduł używany w kodzie skrótu.</span><span class="sxs-lookup"><span data-stu-id="c7806-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="c7806-134">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="c7806-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7806-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7806-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c7806-136">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c7806-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
