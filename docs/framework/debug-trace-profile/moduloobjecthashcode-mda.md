---
title: moduloObjectHashcode MDA
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
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216182"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="0cd19-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="0cd19-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="0cd19-103">`moduloObjectHashcode` zarządzanego asystenta debugowania (MDA) zmienia zachowanie klasy <xref:System.Object>, aby wykonać operację modulo dla kodu skrótu zwracanego przez metodę <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd19-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="0cd19-104">Domyślny moduł dla tego elementu MDA wynosi 1, co powoduje, że <xref:System.Object.GetHashCode%2A> zwrócić wartość 0 dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="0cd19-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0cd19-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="0cd19-105">Symptoms</span></span>  
 <span data-ttu-id="0cd19-106">Po przejściu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR) program nie jest już wykonywany prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="0cd19-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="0cd19-107">Program pobiera nieprawidłowy obiekt z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="0cd19-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="0cd19-108">Kolejność wyliczania na podstawie <xref:System.Collections.Hashtable> ma zmianę, która powoduje przerwanie działania programu.</span><span class="sxs-lookup"><span data-stu-id="0cd19-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="0cd19-109">Dwa obiekty, które były takie same, nie są już równe.</span><span class="sxs-lookup"><span data-stu-id="0cd19-109">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="0cd19-110">Dwa obiekty, które nie są równe, są teraz równe.</span><span class="sxs-lookup"><span data-stu-id="0cd19-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0cd19-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="0cd19-111">Cause</span></span>  
 <span data-ttu-id="0cd19-112">Program może uzyskać niewłaściwy obiekt z <xref:System.Collections.Hashtable>, ponieważ implementacja metody <xref:System.Object.Equals%2A> na klasie dla klucza w <xref:System.Collections.Hashtable> testy pod kątem równości obiektów, porównując wyniki wywołania metody <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd19-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="0cd19-113">Kodów skrótów nie należy używać do testowania równości obiektów, ponieważ dwa obiekty mogą mieć ten sam kod skrótu, nawet jeśli odpowiadające im pola mają różne wartości.</span><span class="sxs-lookup"><span data-stu-id="0cd19-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="0cd19-114">Te konflikty kodu mieszania, chociaż rzadko występują, są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="0cd19-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="0cd19-115">Efekt na wyszukiwaniu <xref:System.Collections.Hashtable> polega na tym, że dwa klucze, które nie są równe, są równe, i zwracany jest nieprawidłowy obiekt z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="0cd19-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="0cd19-116">Ze względu na wydajność implementacja <xref:System.Object.GetHashCode%2A> może ulec zmianie między wersjami środowiska uruchomieniowego, więc kolizje, które mogą nie wystąpić w jednej wersji, mogą wystąpić w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0cd19-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="0cd19-117">Włącz tę funkcję MDA, aby sprawdzić, czy kod ma błędy w przypadku kolizji kodów mieszania.</span><span class="sxs-lookup"><span data-stu-id="0cd19-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="0cd19-118">Gdy ta funkcja jest włączona, to zdarzenie MDA spowoduje zwrócenie wartości 0 przez metodę <xref:System.Object.GetHashCode%2A>, co spowodowało kolizję wszystkich kodów skrótu.</span><span class="sxs-lookup"><span data-stu-id="0cd19-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="0cd19-119">Jedynym efektem włączenia tego pakietu w programie jest to, że program działa wolniej.</span><span class="sxs-lookup"><span data-stu-id="0cd19-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="0cd19-120">Kolejność wyliczania z <xref:System.Collections.Hashtable> może ulec zmianie z jednej wersji środowiska uruchomieniowego na inną, jeśli algorytm używany do obliczania kodów skrótów dla zmiany klucza.</span><span class="sxs-lookup"><span data-stu-id="0cd19-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="0cd19-121">Aby sprawdzić, czy program pobrał zależność od kolejności wyliczania kluczy lub wartości z tabeli skrótów, można włączyć to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="0cd19-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0cd19-122">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="0cd19-122">Resolution</span></span>  
 <span data-ttu-id="0cd19-123">Nigdy nie używaj kodów skrótu jako substytutu dla tożsamości obiektu.</span><span class="sxs-lookup"><span data-stu-id="0cd19-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="0cd19-124">Zaimplementuj przesłonięcie metody <xref:System.Object.Equals%2A?displayProperty=nameWithType>, aby nie porównywać kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="0cd19-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="0cd19-125">Nie należy tworzyć zależności względem kolejności wyliczeń kluczy lub wartości w tabelach skrótów.</span><span class="sxs-lookup"><span data-stu-id="0cd19-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0cd19-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0cd19-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="0cd19-127">Aplikacje działają wolniej, gdy to MDA jest włączone.</span><span class="sxs-lookup"><span data-stu-id="0cd19-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="0cd19-128">To zdarzenie MDA po prostu pobiera zwrócony kod skrótu, a zamiast tego zwraca resztę przy poddzieleniu przez moduł.</span><span class="sxs-lookup"><span data-stu-id="0cd19-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0cd19-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="0cd19-129">Output</span></span>  
 <span data-ttu-id="0cd19-130">Brak danych wyjściowych dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="0cd19-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0cd19-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="0cd19-131">Configuration</span></span>  
 <span data-ttu-id="0cd19-132">Atrybut `modulus` określa moduł używany w kodzie skrótu.</span><span class="sxs-lookup"><span data-stu-id="0cd19-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="0cd19-133">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="0cd19-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cd19-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cd19-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0cd19-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0cd19-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
