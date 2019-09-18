---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93c426cce792c8f30a3551e2d4626736dd67278f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052942"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="e47fe-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="e47fe-102">bindingFailure MDA</span></span>

<span data-ttu-id="e47fe-103">Asystent `bindingFailure` debugowania zarządzanego (MDA) jest uaktywniany w przypadku niepowodzenia ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="e47fe-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="e47fe-104">Symptoms</span></span>

<span data-ttu-id="e47fe-105">Kod podjął próbę załadowania zestawu przy użyciu statycznego odwołania lub jednej z metod Loader, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e47fe-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e47fe-106">Zestaw nie został załadowany i <xref:System.IO.FileNotFoundException> zostanie zgłoszony wyjątek lub. <xref:System.IO.FileLoadException></span><span class="sxs-lookup"><span data-stu-id="e47fe-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="e47fe-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e47fe-107">Cause</span></span>

<span data-ttu-id="e47fe-108">Błąd powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="e47fe-109">Błąd powiązania może wynikać z jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="e47fe-109">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="e47fe-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie może znaleźć żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="e47fe-111">Istnieje wiele powodów, na przykład nieinstalacja zestawu lub aplikacja, która nie jest poprawnie skonfigurowana do znajdowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="e47fe-112">Typowy scenariusz problemu przekazuje typ do innej domeny aplikacji, co wymaga, aby środowisko CLR ładowało zestaw zawierający ten typ w innej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e47fe-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="e47fe-113">Ładowanie zestawu przez środowisko uruchomieniowe może nie być możliwe, jeśli inna domena aplikacji jest skonfigurowana inaczej niż oryginalna domena aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e47fe-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="e47fe-114">Na przykład dwie domeny aplikacji mogą mieć różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e47fe-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="e47fe-115">Żądany zestaw jest uszkodzony lub nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="e47fe-115">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="e47fe-116">Kod próbujący załadować zestaw nie ma poprawnych uprawnień dostępu kodu do ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="e47fe-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="e47fe-117">Poświadczenia użytkownika nie zapewniają wymaganych uprawnień do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="e47fe-117">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="e47fe-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e47fe-118">Resolution</span></span>

<span data-ttu-id="e47fe-119">Pierwszym krokiem jest określenie, dlaczego nie można powiązać środowiska CLR z żądanym zestawem.</span><span class="sxs-lookup"><span data-stu-id="e47fe-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="e47fe-120">Istnieje wiele powodów, dla których środowisko wykonawcze mogło nie zostać odnalezione lub można załadować żądany zestaw, na przykład scenariusze wymienione w sekcji Przyczyna.</span><span class="sxs-lookup"><span data-stu-id="e47fe-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="e47fe-121">Aby wyeliminować przyczynę niepowodzenia powiązania, zaleca się wykonanie następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e47fe-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="e47fe-122">Ustal przyczynę przy użyciu danych dostarczonych przez `bindingFailure` zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="e47fe-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="e47fe-123">Uruchom [Fuslogvw. exe (Podgląd dziennika powiązań zestawów)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) , aby odczytać dzienniki błędów generowane przez spinacz zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="e47fe-124">Ustal, czy zestaw znajduje się w lokalizacji, w której zażądano.</span><span class="sxs-lookup"><span data-stu-id="e47fe-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="e47fe-125">W przypadku <xref:System.Reflection.Assembly.LoadFrom%2A> metod i <xref:System.Reflection.Assembly.LoadFile%2A> można łatwo określić żądaną lokalizację.</span><span class="sxs-lookup"><span data-stu-id="e47fe-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="e47fe-126">W przypadku <xref:System.Reflection.Assembly.Load%2A> metody, która wiąże się przy użyciu tożsamości zestawu, należy wyszukać zestawy, które pasują do tej tożsamości w ścieżce sondy <xref:System.AppDomain.BaseDirectory%2A> właściwości domeny aplikacji i globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e47fe-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="e47fe-127">Rozwiąż przyczynę w oparciu o poprzednie oznaczenie.</span><span class="sxs-lookup"><span data-stu-id="e47fe-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="e47fe-128">Możliwe opcje rozpoznawania są następujące:</span><span class="sxs-lookup"><span data-stu-id="e47fe-128">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="e47fe-129">Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i Wywołaj.</span><span class="sxs-lookup"><span data-stu-id="e47fe-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="e47fe-130"><xref:System.Reflection.Assembly.Load%2A>Metoda ładowania zestawu według tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e47fe-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="e47fe-131">Skopiuj żądany zestaw do katalogu aplikacji i Wywołaj <xref:System.Reflection.Assembly.Load%2A> metodę, aby załadować zestaw według tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e47fe-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="e47fe-132">Skonfiguruj ponownie domenę aplikacji, w której wystąpił błąd powiązania w celu uwzględnienia ścieżki zestawu przez zmianę <xref:System.AppDomain.BaseDirectory%2A> właściwości lub dodanie prywatnych ścieżek do sondowania.</span><span class="sxs-lookup"><span data-stu-id="e47fe-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="e47fe-133">Zmień listę kontroli dostępu dla pliku, aby umożliwić zalogowanemu użytkownikowi odczytywanie pliku.</span><span class="sxs-lookup"><span data-stu-id="e47fe-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="e47fe-134">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e47fe-134">Effect on the Runtime</span></span>

<span data-ttu-id="e47fe-135">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e47fe-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="e47fe-136">Raportuje tylko dane dotyczące niepowodzeń powiązań.</span><span class="sxs-lookup"><span data-stu-id="e47fe-136">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="e47fe-137">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e47fe-137">Output</span></span>

<span data-ttu-id="e47fe-138">Raport MDA zgłasza zestaw, którego nie udało się załadować, w tym żądaną ścieżkę i/lub nazwę wyświetlaną, kontekst powiązania, domenę aplikacji, w której zażądano obciążenia, oraz przyczynę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="e47fe-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="e47fe-139">Nazwa wyświetlana lub żądana ścieżka może być pusta, jeśli te dane nie były dostępne dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e47fe-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="e47fe-140">Jeśli wywołanie, które zakończyło się <xref:System.Reflection.Assembly.Load%2A> niepowodzeniem, prawdopodobnie środowisko uruchomieniowe nie mogło określić nazwy wyświetlanej zestawu.</span><span class="sxs-lookup"><span data-stu-id="e47fe-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="e47fe-141">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e47fe-141">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="e47fe-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="e47fe-142">Example</span></span>

<span data-ttu-id="e47fe-143">Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA:</span><span class="sxs-lookup"><span data-stu-id="e47fe-143">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e47fe-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e47fe-144">See also</span></span>

- [<span data-ttu-id="e47fe-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e47fe-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
