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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a53f433d1b6caca98b2b0d564774820239320f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739670"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="d8aec-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="d8aec-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="d8aec-103">`moduloObjectHashcode` Zarządzanego Asystenta debugowania (MDA) zmienia zachowanie <xref:System.Object> klasy w celu wykonania modulo operacja zwracane przez wartość skrótu <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d8aec-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="d8aec-104">Modulo domyślny dla to zdarzenie MDA wynosi 1, co powoduje, że <xref:System.Object.GetHashCode%2A> do zwrócenia 0 dla wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="d8aec-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d8aec-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="d8aec-105">Symptoms</span></span>  
 <span data-ttu-id="d8aec-106">Po przeniesieniu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR), program nie jest już działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="d8aec-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="d8aec-107">Program będzie niedługo niewłaściwym obiektem z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="d8aec-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="d8aec-108">Kolejność wyliczania z <xref:System.Collections.Hashtable> zmieniło przerwanie wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="d8aec-109">Dwa obiekty, które umożliwiają równe już nie są równe.</span><span class="sxs-lookup"><span data-stu-id="d8aec-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="d8aec-110">Dwa obiekty, które są używane, nie są równe, teraz są równe.</span><span class="sxs-lookup"><span data-stu-id="d8aec-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d8aec-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d8aec-111">Cause</span></span>  
 <span data-ttu-id="d8aec-112">Program może być wprowadzenie niewłaściwym obiektem z <xref:System.Collections.Hashtable> ponieważ implementacja <xref:System.Object.Equals%2A> metodę w klasie klucz do <xref:System.Collections.Hashtable> testuje pod kątem równości obiektów przez porównanie wyników wywołanie <xref:System.Object.GetHashCode%2A> — metoda .</span><span class="sxs-lookup"><span data-stu-id="d8aec-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="d8aec-113">Kody skrótów nie powinien umożliwia testowanie dla równości obiektu, ponieważ dwa obiekty mogą mieć tę samą wartość skrótu, nawet jeśli ich odpowiednich pól mają różne wartości.</span><span class="sxs-lookup"><span data-stu-id="d8aec-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="d8aec-114">Te konflikty kod skrótu, występować sporadycznie w praktyce.</span><span class="sxs-lookup"><span data-stu-id="d8aec-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="d8aec-115">Efekt ten ma na <xref:System.Collections.Hashtable> wyszukiwania jest wyświetlane dwa klucze, które nie są takie same, równe i nieprawidłowy obiekt jest zwracany z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="d8aec-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="d8aec-116">Ze względu na wydajność wdrożenia <xref:System.Object.GetHashCode%2A> może się zmieniać między wersjami środowiska uruchomieniowego, więc mogą wystąpić konflikty, które nie mogą wystąpić w jednej wersji, w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d8aec-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="d8aec-117">Włącz to zdarzenie MDA sprawdzić, czy kod ma błędy, gdy kolizji kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="d8aec-118">Po włączeniu to zdarzenie MDA powoduje, że <xref:System.Object.GetHashCode%2A> metody zwracają 0, co wszystkie kody skrótów kolizji.</span><span class="sxs-lookup"><span data-stu-id="d8aec-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="d8aec-119">Jedynie wpływ Włączanie to zdarzenie MDA powinien już z programu jest spowolnienie działania Twojego programu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="d8aec-120">Kolejność wyliczania z <xref:System.Collections.Hashtable> mogą ulec zmianie z jednej wersji środowiska uruchomieniowego, jeśli inny algorytm używany do obliczania kodów skrótu dla zmian klucza.</span><span class="sxs-lookup"><span data-stu-id="d8aec-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="d8aec-121">Aby sprawdzić, czy program miało zależności kolejności wyliczenie kluczy i wartości z tabeli wyznaczania wartości skrótu, aby umożliwić to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="d8aec-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d8aec-122">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d8aec-122">Resolution</span></span>  
 <span data-ttu-id="d8aec-123">Nigdy nie używaj kody skrótów zastępuje tożsamość obiektu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="d8aec-124">Implementowanie zastępowania metody <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda porównuje kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="d8aec-125">Nie należy tworzyć zależności w kolejności wyliczenia o kluczy ani wartości w tabelach wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d8aec-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d8aec-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="d8aec-127">Aplikacje działają wolniej, po włączeniu to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="d8aec-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="d8aec-128">To zdarzenie MDA po prostu przyjmuje skrótu, który będzie zwracany i zamiast tego zwraca resztę z dzielenia podzielone przez moduł.</span><span class="sxs-lookup"><span data-stu-id="d8aec-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d8aec-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d8aec-129">Output</span></span>  
 <span data-ttu-id="d8aec-130">Nie ma żadnych danych wyjściowych dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="d8aec-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d8aec-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d8aec-131">Configuration</span></span>  
 <span data-ttu-id="d8aec-132">`modulus` Atrybut określa modulo na wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8aec-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="d8aec-133">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="d8aec-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8aec-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8aec-134">See also</span></span>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d8aec-135">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d8aec-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
