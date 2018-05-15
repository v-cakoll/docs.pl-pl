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
ms.openlocfilehash: 1a75efaf6703858fdb48a3f09635da1be4463d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="8a8cf-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="8a8cf-102">bindingFailure MDA</span></span>
<span data-ttu-id="8a8cf-103">`bindingFailure` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy zestaw nie udało się załadować.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8a8cf-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="8a8cf-104">Symptoms</span></span>  
 <span data-ttu-id="8a8cf-105">Kod podjął próbę załadowania zestawu przy użyciu odwołanie statyczne lub jednej z metod modułu ładującego, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8a8cf-106">Zestaw nie został załadowany i <xref:System.IO.FileNotFoundException> lub <xref:System.IO.FileLoadException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8a8cf-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="8a8cf-107">Cause</span></span>  
 <span data-ttu-id="8a8cf-108">Niepowodzenie powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="8a8cf-109">Niepowodzenie powiązania może być skutkiem jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="8a8cf-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="8a8cf-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie można odnaleźć żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="8a8cf-111">Istnieje wiele przyczyn, może to się zdarzyć, takich jak zestaw nie jest zainstalowany lub aplikacja nie jest poprawnie skonfigurowana można znaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="8a8cf-112">Typowy scenariusz problemu jest przekazanie typu do innej domeny aplikacji, co wymaga CLR można załadować zestawu zawierającego tego typu w innej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="8a8cf-113">Nie być może środowiska uruchomieniowego można załadować zestawu, jeśli domena aplikacji jest inaczej skonfigurowana od oryginalnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="8a8cf-114">Na przykład domen aplikacji dwóch mają różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="8a8cf-115">Żądany zestaw jest uszkodzony lub nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="8a8cf-116">Podjęto próbę załadowania zestawu kod nie ma uprawnienia zabezpieczeń dostępu kodu poprawne ładowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="8a8cf-117">Poświadczenia użytkownika nie zapewniają wymagane uprawnienia do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8a8cf-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8a8cf-118">Resolution</span></span>  
 <span data-ttu-id="8a8cf-119">Pierwszym krokiem jest ustalenie, dlaczego CLR nie można powiązać żądany zestaw.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="8a8cf-120">Istnieje wiele przyczyn, dlaczego środowiska uruchomieniowego nie zostały znalezione lub został stanie obciążenia żądany zestaw, takich jak scenariusze opisane w sekcji Przyczyna.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="8a8cf-121">Aby wyeliminować przyczynę niepowodzenia powiązania zalecane są następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="8a8cf-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="8a8cf-122">Ustal przyczynę przy użyciu danych dostarczonych przez `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="8a8cf-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="8a8cf-123">Uruchom [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) odczytać dzienniki błędów, utworzonego przez obiekt wiążący zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="8a8cf-124">Ustal, jeśli zestaw w lokalizacji jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="8a8cf-125">W przypadku liczby <xref:System.Reflection.Assembly.LoadFrom%2A> i <xref:System.Reflection.Assembly.LoadFile%2A> metod, żądanej lokalizacji można łatwo ustalić.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="8a8cf-126">W przypadku liczby <xref:System.Reflection.Assembly.Load%2A> metodę, która wiąże przy użyciu tożsamości zestawu, musisz sprawdzić dla zestawów zgodnych jego tożsamość w domenie aplikacji <xref:System.AppDomain.BaseDirectory%2A> ścieżka sondowania właściwości i globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="8a8cf-127">Usuń przyczynę oparte na poprzednie określenie.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="8a8cf-128">Opcje rozpoznawania możliwe są następujące:</span><span class="sxs-lookup"><span data-stu-id="8a8cf-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="8a8cf-129">Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i wywołania.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="8a8cf-130"><xref:System.Reflection.Assembly.Load%2A> Metoda ładowania zestawu przez tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="8a8cf-131">Skopiuj żądany zestaw do katalogu aplikacji i wywołanie <xref:System.Reflection.Assembly.Load%2A> metodę, aby załadować zestawu przez tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="8a8cf-132">Skonfiguruj ponownie domeny aplikacji, w którym wystąpił błąd powiązania uwzględnienie ścieżkę zestawu albo zmieniając <xref:System.AppDomain.BaseDirectory%2A> właściwości lub Dodawanie prywatnej sondowania ścieżek.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="8a8cf-133">Zmiana listy kontroli dostępu dla plików umożliwiają zalogowanego użytkownika do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8a8cf-134">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8a8cf-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="8a8cf-135">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8a8cf-136">Zwraca tylko dane o powiązanie błędów.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8a8cf-137">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8a8cf-137">Output</span></span>  
 <span data-ttu-id="8a8cf-138">MDA raporty zestawu, którego nie udało się załadować, w tym żądana ścieżka lub nazwa wyświetlana, kontekst powiązania, domena aplikacji, w której zażądano obciążenia i przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="8a8cf-139">Żądana ścieżka lub nazwa wyświetlana może być pusta, jeśli dane nie był dostępny do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="8a8cf-140">Jeśli wywołanie, której nie można było <xref:System.Reflection.Assembly.Load%2A> — metoda, prawdopodobnie środowiska uruchomieniowego nie można ustalić nazwę wyświetlaną dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a8cf-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8a8cf-141">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8a8cf-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="8a8cf-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a8cf-142">Example</span></span>  
 <span data-ttu-id="8a8cf-143">W poniższym przykładzie kodu pokazano sytuację, której można uaktywnić to zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="8a8cf-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="8a8cf-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a8cf-144">See Also</span></span>  
 [<span data-ttu-id="8a8cf-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="8a8cf-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
