---
title: Wyjątki czasu wykonywania w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed019dc4f1e6b99c9fa1d001c94af45802336ba6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715519"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="90e8c-102">Wyjątki czasu wykonywania w aplikacjach .NET Native</span><span class="sxs-lookup"><span data-stu-id="90e8c-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="90e8c-103">Jest ważne przetestować kompilacji wydania aplikacji Universal Windows Platform na ich platformach docelowych, ponieważ konfiguracji debug i release całkowicie różnią się.</span><span class="sxs-lookup"><span data-stu-id="90e8c-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="90e8c-104">Domyślnie korzysta z konfiguracji debugowania środowiska uruchomieniowego .NET Core do kompilowania aplikacji, ale konfiguracja wydania używa platformy .NET Native do kompilowania aplikacji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="90e8c-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90e8c-105">Aby uzyskać informacje w sprawach związanych z [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, które użytkownik może Podczas testowania wersji aplikacji, zobacz "krok 4: Ręcznie rozwiązać Brak metadanych: w [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md) tematu, a także [odbicia i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) i [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="90e8c-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="90e8c-106">Kompilacje debugowania i wydania</span><span class="sxs-lookup"><span data-stu-id="90e8c-106">Debug and release builds</span></span>  
 <span data-ttu-id="90e8c-107">Jeśli kompilacja debugowania jest wykonywana względem czasu wykonywania platformy .NET Core, nie został wcześniej skompilowany na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="90e8c-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="90e8c-108">To sprawia, że wszystkie usługi, zazwyczaj dostarczane przez środowisko uruchomieniowe dostępna dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90e8c-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="90e8c-109">Z drugiej strony kompilację wydania kompiluje do kodu natywnego dla swojej platformy docelowe, usuwa większość zależności zewnętrznych środowisk uruchomieniowych i bibliotek i intensywnie optymalizuje kod, aby osiągnąć najwyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="90e8c-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="90e8c-110">Podczas debugowania kompilacji wydania, które są kompilowane przy użyciu platformy .NET Native:</span><span class="sxs-lookup"><span data-stu-id="90e8c-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="90e8c-111">Możesz użyć platformy .NET Native aparat debugowania, który różni się od normalnych .NET, narzędzia debugowania.</span><span class="sxs-lookup"><span data-stu-id="90e8c-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="90e8c-112">Rozmiar plik wykonywalny zmniejsza się w miarę możliwości.</span><span class="sxs-lookup"><span data-stu-id="90e8c-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="90e8c-113">Jednym ze sposobów .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinania komunikaty wyjątku środowiska uruchomieniowego, w temacie omówiono bardziej szczegółowo w [komunikaty o wyjątkach środowiska uruchomieniowego](#Messages) sekcji.</span><span class="sxs-lookup"><span data-stu-id="90e8c-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="90e8c-114">Twój kod intensywnie jest zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="90e8c-114">Your code is heavily optimized.</span></span> <span data-ttu-id="90e8c-115">Oznacza to, że wbudowanie jest używana zawsze, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="90e8c-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="90e8c-116">(Wbudowanie przenosi kod z procedur zewnętrznych do wywoływania procedury.)   Fakt, że .NET Native udostępnia wyspecjalizowane środowiska uruchomieniowego i implementuje agresywne wbudowanie wpływa na stos wywołań, który jest wyświetlany podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="90e8c-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="90e8c-117">Aby uzyskać więcej informacji, zobacz [stosu środowiska uruchomieniowego](#CallStack) sekcji.</span><span class="sxs-lookup"><span data-stu-id="90e8c-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e8c-118">Można kontrolować, czy debug i release kompilacje są kompilowane przy użyciu łańcucha narzędzi .NET Native przez zaznaczenie lub usunięcie zaznaczenia **kompilacji z łańcucha narzędzi .NET Native** pole.</span><span class="sxs-lookup"><span data-stu-id="90e8c-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="90e8c-119">Należy jednak pamiętać, że Store Windows zawsze zostanie skompilowany w wersję produkcyjną aplikacji przy użyciu platformy .NET Native łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="90e8c-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="90e8c-120">Komunikaty o wyjątkach środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="90e8c-120">Runtime exception messages</span></span>  
 <span data-ttu-id="90e8c-121">Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie obejmuje pełny tekst komunikaty o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="90e8c-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="90e8c-122">W rezultacie wyjątki środowiska uruchomieniowego zgłoszony w wydawanych wersjach mogą nie wyświetlać pełny tekst komunikaty o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="90e8c-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="90e8c-123">Zamiast tego tekstu może składać się podciągu wraz z linkiem do wykonania, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="90e8c-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="90e8c-124">Na przykład informacje o wyjątku może pojawić się jako:</span><span class="sxs-lookup"><span data-stu-id="90e8c-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="90e8c-125">Jeśli potrzebujesz komunikat o wyjątku pełną, należy uruchomić kompilację debugowania.</span><span class="sxs-lookup"><span data-stu-id="90e8c-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="90e8c-126">Na przykład poprzednie informacje o wyjątku z kompilacji wydania może wyglądać następująco w kompilacji debugowania:</span><span class="sxs-lookup"><span data-stu-id="90e8c-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="90e8c-127">Stos wywołań środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="90e8c-127">Runtime call stack</span></span>  
 <span data-ttu-id="90e8c-128">Ze względu na wbudowanie i inne optymalizacje stos wywołań, wyświetlany przez aplikację, skompilowany przez łańcuch narzędzi .NET Native nie mogą pomóc Ci celu jednoznacznego zidentyfikowania ścieżkę do wyjątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="90e8c-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="90e8c-129">Aby uzyskać pełny stos, należy zamiast tego należy uruchomić z kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="90e8c-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e8c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90e8c-130">See also</span></span>
- [<span data-ttu-id="90e8c-131">Debugowanie aplikacji Universal Windows natywnych platformy .NET</span><span class="sxs-lookup"><span data-stu-id="90e8c-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="90e8c-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="90e8c-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
