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
ms.openlocfilehash: 88f23c2e03966bffccc9153e18e1b54e6847987d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127611"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="3f244-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="3f244-102">bindingFailure MDA</span></span>
<span data-ttu-id="3f244-103">`bindingFailure` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy zestaw nie udało się załadować.</span><span class="sxs-lookup"><span data-stu-id="3f244-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3f244-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="3f244-104">Symptoms</span></span>  
 <span data-ttu-id="3f244-105">Kod podjął próbę załadowania zestawu przy użyciu statyczne odwołanie lub jednej z metod modułu ładującego, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f244-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f244-106">Zestaw nie jest załadowany i <xref:System.IO.FileNotFoundException> lub <xref:System.IO.FileLoadException> jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3f244-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3f244-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3f244-107">Cause</span></span>  
 <span data-ttu-id="3f244-108">Niepowodzenie powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f244-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="3f244-109">Niepowodzenie powiązania mogą wynikać z jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="3f244-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="3f244-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie można odnaleźć żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f244-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="3f244-111">Istnieje wiele przyczyn, że taka sytuacja może wystąpić, np. zestaw nie jest zainstalowany lub aplikacja nie jest prawidłowo skonfigurowane do znajdowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f244-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="3f244-112">Typowy scenariusz problemu to przekazanie typu do innej domeny aplikacji, co wymaga środowiska CLR do załadowania zestawu zawierającego tego typu w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f244-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="3f244-113">Może nie być możliwe dla środowiska uruchomieniowego do załadowania zestawu, jeśli domena aplikacji jest inaczej skonfigurowana od oryginalnego domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f244-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="3f244-114">Na przykład, obu domen aplikacji może mieć różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3f244-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="3f244-115">Żądany zestaw jest uszkodzony lub nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="3f244-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="3f244-116">Kod próby załadowania zestawu nie ma uprawnienia zabezpieczeń dostępu kodu poprawne ładować zestawy.</span><span class="sxs-lookup"><span data-stu-id="3f244-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="3f244-117">Poświadczenia użytkownika nie są oferowane wymaganych uprawnień do odczytu tego pliku.</span><span class="sxs-lookup"><span data-stu-id="3f244-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3f244-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3f244-118">Resolution</span></span>  
 <span data-ttu-id="3f244-119">Pierwszym krokiem jest ustalenie, dlaczego CLR nie można powiązać żądany zestaw.</span><span class="sxs-lookup"><span data-stu-id="3f244-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="3f244-120">Istnieje wiele powodów, dlaczego środowisko wykonawcze nie zostały znalezione lub został stanie obciążenia żądany zestaw, takich jak scenariusze opisane w sekcji Przyczyna.</span><span class="sxs-lookup"><span data-stu-id="3f244-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="3f244-121">Aby wyeliminować przyczynę niepowodzenia powiązania, zaleca się następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="3f244-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="3f244-122">Ustalić przyczynę przy użyciu danych udostępnionych przez `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="3f244-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="3f244-123">Uruchom [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) odczytać dzienniki błędów, generowane przez binder zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f244-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="3f244-124">Określ, jeśli zestaw znajduje się w lokalizacji, na żądanie.</span><span class="sxs-lookup"><span data-stu-id="3f244-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="3f244-125">W przypadku właściwości <xref:System.Reflection.Assembly.LoadFrom%2A> i <xref:System.Reflection.Assembly.LoadFile%2A> można łatwo określić metod, żądanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3f244-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="3f244-126">W przypadku właściwości <xref:System.Reflection.Assembly.Load%2A> metody, która wiąże przy użyciu tożsamości zestawu, musisz sprawdzić dla zestawów, które odpowiadają tej tożsamości w domenie aplikacji <xref:System.AppDomain.BaseDirectory%2A> ścieżka sondy właściwości i globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3f244-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="3f244-127">Rozwiąż przyczynę oparte na określenie poprzedniej.</span><span class="sxs-lookup"><span data-stu-id="3f244-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="3f244-128">Opcje rozpoznawania możliwe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3f244-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="3f244-129">Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i wywołania.</span><span class="sxs-lookup"><span data-stu-id="3f244-129">Install the requested assembly in the global assembly cache and call the.</span></span> <xref:System.Reflection.Assembly.Load%2A> <span data-ttu-id="3f244-130">Metoda można załadować zestawu przez tożsamość.</span><span class="sxs-lookup"><span data-stu-id="3f244-130">method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="3f244-131">Skopiuj żądany zestaw do katalogu aplikacji i wywołanie <xref:System.Reflection.Assembly.Load%2A> metodę, aby załadować zestaw przez tożsamość.</span><span class="sxs-lookup"><span data-stu-id="3f244-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="3f244-132">Ponownie skonfiguruj domenę aplikacji, w którym wystąpił błąd powiązania obejmujący ścieżkę zestawu, wprowadzając dowolną zmianę <xref:System.AppDomain.BaseDirectory%2A> właściwości lub dodawanie prywatnych ścieżkach sondowania.</span><span class="sxs-lookup"><span data-stu-id="3f244-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="3f244-133">Zmiana listy kontroli dostępu do pliku umożliwić zalogowanego użytkownika można odczytać pliku.</span><span class="sxs-lookup"><span data-stu-id="3f244-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3f244-134">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3f244-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="3f244-135">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="3f244-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="3f244-136">Informuje jedynie dane o powiązaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="3f244-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3f244-137">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3f244-137">Output</span></span>  
 <span data-ttu-id="3f244-138">MDA raporty zestawu, który nie udało się załadować, w tym żądana ścieżka lub nazwa wyświetlana, kontekstu powiązania, domeny aplikacji, w której zażądano obciążenia i przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="3f244-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="3f244-139">Żądana ścieżka lub nazwa wyświetlana może być pusta, jeśli te dane są niedostępne do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3f244-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="3f244-140">Jeśli było wywołanie, który uległ awarii <xref:System.Reflection.Assembly.Load%2A> metoda, prawdopodobnie środowisko wykonawcze nie można określić nazwę wyświetlaną dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f244-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3f244-141">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="3f244-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="3f244-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f244-142">Example</span></span>  
 <span data-ttu-id="3f244-143">W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="3f244-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f244-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f244-144">See also</span></span>

- [<span data-ttu-id="3f244-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3f244-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
