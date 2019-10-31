---
title: Analizatory zabezpieczeń .NET — .NET
description: Dowiedz się, jak używać analizatorów zabezpieczeń .NET w pakiecie analizatorów .NET Framework, aby znajdować i rozwiązywać zagrożenia bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 03268375739b34a43f38c60fbfd2c993da9f3840
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197966"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="97c47-103">Analizator .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97c47-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="97c47-104">Możesz użyć analizatora .NET Framework, aby znaleźć potencjalne problemy w kodzie aplikacji opartym na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97c47-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="97c47-105">Ten Analizator odnajdzie potencjalne problemy i sugeruje do nich poprawki.</span><span class="sxs-lookup"><span data-stu-id="97c47-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="97c47-106">Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="97c47-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="97c47-107">Należy dodać Analizator do projektu tak szybko, jak to możliwe w rozwoju.</span><span class="sxs-lookup"><span data-stu-id="97c47-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="97c47-108">Wkrótce znajdziesz ewentualne potencjalne problemy w kodzie, tym łatwiejsze jest ich naprawa.</span><span class="sxs-lookup"><span data-stu-id="97c47-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="97c47-109">Można jednak dodać go w dowolnym momencie w cyklu projektowania.</span><span class="sxs-lookup"><span data-stu-id="97c47-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="97c47-110">Znajduje wszelkie problemy związane z istniejącym kodem i ostrzega o nowych problemach związanych z programowaniem.</span><span class="sxs-lookup"><span data-stu-id="97c47-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="97c47-111">Instalowanie i Konfigurowanie analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97c47-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="97c47-112">Analizatory zabezpieczeń .NET muszą być zainstalowane jako pakiet NuGet w każdym projekcie, w którym mają być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="97c47-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="97c47-113">Tylko jeden Deweloper musi dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="97c47-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="97c47-114">Pakiet analizatora jest zależnością projektu i będzie działać na każdym komputerze dewelopera, gdy ma zaktualizowane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="97c47-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="97c47-115">Analizator .NET Framework jest dostarczany w pakiecie NuGet [Microsoft. NETFramework. analizators](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) .</span><span class="sxs-lookup"><span data-stu-id="97c47-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="97c47-116">Ten pakiet zawiera tylko analizatory charakterystyczne dla .NET Framework, które obejmują analizatory zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="97c47-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="97c47-117">W większości przypadków należy użyć pakietu NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .</span><span class="sxs-lookup"><span data-stu-id="97c47-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="97c47-118">Pakiet zagregowany FxCopAnalyzers zawiera wszystkie analizatory struktury zawarte w pakiecie Framework. analizatory, a także następujące analizatory:</span><span class="sxs-lookup"><span data-stu-id="97c47-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="97c47-119">[Microsoft. CodeQuality. analizatory](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): zawiera ogólne wskazówki i wskazówki dotyczące .NET Standard interfejsów API</span><span class="sxs-lookup"><span data-stu-id="97c47-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="97c47-120">[Microsoft. rdzeń. analizatory](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): udostępnia analizatory charakterystyczne dla interfejsów API platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="97c47-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="97c47-121">[Text. analizatory](https://www.nuget.org/packages/Text.Analyzers): zawiera wskazówki dotyczące tekstu zawartego w kodzie, w tym komentarzy.</span><span class="sxs-lookup"><span data-stu-id="97c47-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="97c47-122">Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz polecenie "Zarządzaj zależnościami".</span><span class="sxs-lookup"><span data-stu-id="97c47-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="97c47-123">W Eksploratorze NuGet Wyszukaj ciąg "NetFramework Analyzer" lub, jeśli wolisz, "FX COP Analyzer".</span><span class="sxs-lookup"><span data-stu-id="97c47-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="97c47-124">Zainstaluj najnowszą stabilną wersję we wszystkich projektach w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="97c47-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="97c47-125">Korzystanie z analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97c47-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="97c47-126">Po zainstalowaniu pakietu NuGet Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="97c47-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="97c47-127">Analizator zgłosi wszelkie problemy, które znajdują się w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="97c47-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="97c47-128">Problemy są raportowane jako ostrzeżenia w oknie Lista błędów programu Visual Studio, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="97c47-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemy zgłoszone przez analizator Framework](./media/framework-analyzers-2.png)

<span data-ttu-id="97c47-130">Podczas pisania kodu zobaczysz zygzaki poniżej dowolnego potencjalnego problemu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="97c47-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="97c47-131">Umieść wskaźnik myszy nad dowolnym problemem i Wyświetl szczegóły dotyczące problemu oraz sugestie dotyczące ewentualnych poprawek, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="97c47-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktywny raport o problemach znalezionych przez analizator Framework](./media/framework-analyzers-1.png)

<span data-ttu-id="97c47-133">Analizatory sprawdzają kod w rozwiązaniu i zapewniają listę ostrzeżeń dla dowolnego z następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="97c47-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="97c47-134">CA1058: Typy nie powinny rozszerzać pewnych typów bazowych</span><span class="sxs-lookup"><span data-stu-id="97c47-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="97c47-135">Istnieje niewielka liczba typów w .NET Framework, które nie powinny być bezpośrednio wyprowadzane.</span><span class="sxs-lookup"><span data-stu-id="97c47-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="97c47-136">**Kategoria:** Zdefiniowanych</span><span class="sxs-lookup"><span data-stu-id="97c47-136">**Category:** Design</span></span>

<span data-ttu-id="97c47-137">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-137">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-138">Informacje dodatkowe: [CA: 1058: typy nie powinny poszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="97c47-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="97c47-139">CA2153: nie Przechwytuj wyjątków uszkodzonych Stanów</span><span class="sxs-lookup"><span data-stu-id="97c47-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="97c47-140">Przechwycenie wyjątków uszkodzonego stanu może maskować błędy (takie jak naruszenia zasad dostępu), co spowodowało niespójny stan wykonywania lub ułatwianie atakującemu naruszenia bezpieczeństwa systemu.</span><span class="sxs-lookup"><span data-stu-id="97c47-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="97c47-141">Zamiast tego należy przechwycić i obsłużyć bardziej szczegółowy zestaw typów wyjątków lub ponownie zgłosić wyjątek</span><span class="sxs-lookup"><span data-stu-id="97c47-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="97c47-142">**Kategoria:** Bezpieczeństw</span><span class="sxs-lookup"><span data-stu-id="97c47-142">**Category:** Security</span></span>

<span data-ttu-id="97c47-143">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-143">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-144">Informacje dodatkowe: [# # CA2153: nie należy przechwytywać uszkodzonych wyjątków stanu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="97c47-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="97c47-145">CA2229: Należy zaimplementować konstruktory serializacji</span><span class="sxs-lookup"><span data-stu-id="97c47-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="97c47-146">Analizator generuje to ostrzeżenie podczas tworzenia typu, który implementuje interfejs <xref:System.Runtime.Serialization.ISerializable>, ale nie definiuje wymaganego konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="97c47-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="97c47-147">Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="97c47-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="97c47-148">Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.</span><span class="sxs-lookup"><span data-stu-id="97c47-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="97c47-149">Konstruktor serializacji ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="97c47-149">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="97c47-150">**Kategoria:** Wykorzystywani</span><span class="sxs-lookup"><span data-stu-id="97c47-150">**Category:** Usage</span></span>

<span data-ttu-id="97c47-151">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-151">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-152">Informacje dodatkowe: [CA2229: Implementuj konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="97c47-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="97c47-153">CA2235: Należy oznaczyć wszystkie nieserializowane pola</span><span class="sxs-lookup"><span data-stu-id="97c47-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="97c47-154">Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="97c47-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="97c47-155">Należy jawnie oznaczyć to pole z <xref:System.NonSerializedAttribute>, aby usunąć to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="97c47-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="97c47-156">**Kategoria:** Wykorzystywani</span><span class="sxs-lookup"><span data-stu-id="97c47-156">**Category:** Usage</span></span>

<span data-ttu-id="97c47-157">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-157">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-158">Informacje dodatkowe: [CA2235: Oznacz wszystkie pola, które nie są możliwe do serializacji](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="97c47-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="97c47-159">CA2237: Oznacz typy ISerializable z możliwością serializacji</span><span class="sxs-lookup"><span data-stu-id="97c47-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="97c47-160">Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone przy użyciu atrybutu <xref:System.SerializableAttribute>, nawet gdy typ używa niestandardowej procedury serializacji przez implementację interfejsu <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="97c47-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="97c47-161">**Kategoria:** Wykorzystywani</span><span class="sxs-lookup"><span data-stu-id="97c47-161">**Category:** Usage</span></span>

<span data-ttu-id="97c47-162">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-162">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-163">Informacje dodatkowe: [CA2237: Oznacz typy ISerializable z](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute) możliwością serializacji</span><span class="sxs-lookup"><span data-stu-id="97c47-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="97c47-164">CA3075: niezabezpieczone przetwarzanie DTD w kodzie XML</span><span class="sxs-lookup"><span data-stu-id="97c47-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="97c47-165">W przypadku używania niezabezpieczonych wystąpień <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> lub odwołań do zewnętrznych źródeł jednostek Analizator może akceptować niezaufane dane wejściowe i ujawniać poufne informacje osobom atakującym.</span><span class="sxs-lookup"><span data-stu-id="97c47-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="97c47-166">**Kategoria:** Bezpieczeństw</span><span class="sxs-lookup"><span data-stu-id="97c47-166">**Category:** Security</span></span>

<span data-ttu-id="97c47-167">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-167">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-168">Informacje dodatkowe: [A3075: niezabezpieczone przetwarzanie DTD w XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="97c47-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="97c47-169">CA5350: nie używaj słabych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="97c47-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="97c47-170">Algorytmy kryptograficzne obniżają wydajność w miarę upływu czasu, ponieważ ataki stają się bardziej zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="97c47-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="97c47-171">W zależności od typu i zastosowania tego algorytmu kryptograficznego, dalsze obniżenie jego siły kryptograficznej może pozwolić atakującemu na odczytywanie komunikatów ENCIPHERED, manipulowanie komunikatami ENCIPHERED, fałszowanie podpisów cyfrowych, manipulowanie skrótem zawartości lub w przeciwnym razie naruszyć wszelkie cryptosystem na podstawie tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="97c47-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="97c47-172">W przypadku szyfrowania należy użyć algorytmu AES (AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="97c47-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="97c47-173">W celu utworzenia skrótu należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA-2 512, SHA-2 384 lub SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="97c47-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="97c47-174">**Kategoria:** Bezpieczeństw</span><span class="sxs-lookup"><span data-stu-id="97c47-174">**Category:** Security</span></span>

<span data-ttu-id="97c47-175">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-175">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-176">Informacje dodatkowe: [CA5350: nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="97c47-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="97c47-177">CA5351: nie używaj uszkodzonych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="97c47-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="97c47-178">Atak polegający na tym, że istnieje możliwość obliczeniowa tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="97c47-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="97c47-179">Dzięki temu osoby atakujące mogą zerwać gwarancje kryptograficzne, które są przeznaczone do zapewnienia.</span><span class="sxs-lookup"><span data-stu-id="97c47-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="97c47-180">W zależności od typu i zastosowania tego algorytmu kryptograficznego może to umożliwić osobom atakującym odczytywanie komunikatów ENCIPHERED, manipulowanie komunikatami ENCIPHERED, fałszowanie podpisów cyfrowych, manipulowanie skrótem zawartości lub w inny sposób naruszenie jakichkolwiek cryptosystem na podstawie dla tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="97c47-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="97c47-181">W przypadku szyfrowania należy użyć algorytmu AES (AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="97c47-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="97c47-182">W celu utworzenia skrótów Użyj funkcji tworzenia skrótów w rodzinie SHA-2, takiej jak SHA512, SHA384 lub SHA256.</span><span class="sxs-lookup"><span data-stu-id="97c47-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="97c47-183">W przypadku podpisów cyfrowych należy użyć klucza RSA o długości większej lub równej 2048-bitowej lub ECDSA z długością klucza większą lub równą 256 bitów.</span><span class="sxs-lookup"><span data-stu-id="97c47-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="97c47-184">**Kategoria:** Bezpieczeństw</span><span class="sxs-lookup"><span data-stu-id="97c47-184">**Category:** Security</span></span>

<span data-ttu-id="97c47-185">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="97c47-185">**Severity:** Warning</span></span>

<span data-ttu-id="97c47-186">Informacje dodatkowe: [CA5351: nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="97c47-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
