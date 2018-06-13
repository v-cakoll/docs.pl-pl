---
title: Analizatory zabezpieczeń .NET - .NET
description: Używanie analizatorów zabezpieczeń .NET w pakiecie programu .NET Framework analizatorów znaleźć i zagrożenia bezpieczeństwa
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 904218c177ea45f82a73b4532ce3230af954aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574624"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="93015-103">Analizator Framework .NET</span><span class="sxs-lookup"><span data-stu-id="93015-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="93015-104">Analizator Framework .NET umożliwia znaleźć potencjalnych problemów w kodzie aplikacji opartych na programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93015-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="93015-105">Ta analizator znajduje potencjalne problemy, a także sugeruje rozwiązania ich.</span><span class="sxs-lookup"><span data-stu-id="93015-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="93015-106">Analizatora interaktywnie działa w programie Visual Studio podczas pisania kodu lub w ramach elementu konfiguracji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="93015-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="93015-107">Przy projektowaniu, należy dodać analizatora możliwie jak najszybciej do projektu.</span><span class="sxs-lookup"><span data-stu-id="93015-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="93015-108">Wcześniej odnaleźć dotyczących potencjalnych problemów w kodzie, tym łatwiej są Aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="93015-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="93015-109">Jednak można go dodać w dowolnym momencie w cyklu programowania.</span><span class="sxs-lookup"><span data-stu-id="93015-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="93015-110">Jego znajduje problemy z istniejącego kodu i ostrzeganie o nowe problemy, jak zachować opracowywania.</span><span class="sxs-lookup"><span data-stu-id="93015-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="93015-111">Instalowanie i konfigurowanie analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="93015-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="93015-112">Analizatory zabezpieczeń .NET musi być zainstalowany jako pakietu NuGet, na każdy projekt, gdzie chcesz je uruchomić.</span><span class="sxs-lookup"><span data-stu-id="93015-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="93015-113">Tylko jeden deweloper musi je dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="93015-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="93015-114">Pakiet Analizator jest zależności projektu i zostanie uruchomiony na maszynie Każdy deweloper, gdy ma ona zaktualizowane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="93015-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="93015-115">Analizator Framework .NET jest dostarczany w [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="93015-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="93015-116">Ten pakiet zawiera określone analizatorów programu .NET Framework, w tym analizatorów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="93015-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="93015-117">W większości przypadków należy [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="93015-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="93015-118">Pakiet agregacji FxCopAnalyzers zawiera analizatorów framework zawarte w pakiecie Framework.Analyzers, jak również analizatory następujące:</span><span class="sxs-lookup"><span data-stu-id="93015-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="93015-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API architektury .NET</span><span class="sxs-lookup"><span data-stu-id="93015-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="93015-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): zawiera analizatorów określonych do interfejsów API architektury .NET Core.</span><span class="sxs-lookup"><span data-stu-id="93015-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="93015-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): znajdują się wskazówki dotyczące tekstu jako kod, w tym komentarzy.</span><span class="sxs-lookup"><span data-stu-id="93015-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="93015-122">Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz pozycję "Zarządzaj zależności".</span><span class="sxs-lookup"><span data-stu-id="93015-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="93015-123">W Eksploratorze NuGet, wyszukaj "NetFramework analizator", lub jeśli wolisz "Fx Cop analizator".</span><span class="sxs-lookup"><span data-stu-id="93015-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="93015-124">Zainstaluj najnowszą wersję stabilna ze wszystkich projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="93015-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="93015-125">Za pomocą analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="93015-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="93015-126">Po zainstalowaniu pakietu NuGet, Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="93015-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="93015-127">Analizatora będzie Zgłoś wszelkie problemy, które klient zlokalizuje baza kodu.</span><span class="sxs-lookup"><span data-stu-id="93015-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="93015-128">Problemy są raportowane klientowi jako ostrzeżenia w oknie Lista błędów w usłudze Visual Studio, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="93015-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemy zgłoszone przez analizator framework](./media/framework-analyzers-2.png)

<span data-ttu-id="93015-130">Podczas pisania kodu, zobaczysz zygzaki poniżej wszelkie potencjalne problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="93015-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="93015-131">Umieść kursor nad jakikolwiek problem, i zobaczyć szczegółowe informacje o problemie i sugestie dotyczące wszystkie możliwe rozwiązanie, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="93015-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interakcyjny raport problemów wykrytych przez analizatora framework](./media/framework-analyzers-1.png)

<span data-ttu-id="93015-133">Analizatory badanie kodu w rozwiązaniu i udostępnić listę ostrzeżeń dla każdego z tych problemów:</span><span class="sxs-lookup"><span data-stu-id="93015-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="93015-134">CA1058: Typy nie powinny rozszerzać pewnych typów bazowych</span><span class="sxs-lookup"><span data-stu-id="93015-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="93015-135">Istnieje niewielka liczba typów w programie .NET Framework należy nie pochodzi od bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="93015-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="93015-136">**Kategoria:** projektu</span><span class="sxs-lookup"><span data-stu-id="93015-136">**Category:** Design</span></span>

<span data-ttu-id="93015-137">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-137">**Severity:** Warning</span></span>

<span data-ttu-id="93015-138">Informacje dodatkowe: [CA:1058: typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="93015-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="93015-139">CA2153: Nie Przechwytuj wyjątki uszkodzony</span><span class="sxs-lookup"><span data-stu-id="93015-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="93015-140">Połowowe wyjątki uszkodzony można zamaskować błędy (np. naruszenia zasad dostępu), co w stanie niespójnym wykonywania lub ułatwieniu osobom atakującym naruszyć bezpieczeństwo systemu.</span><span class="sxs-lookup"><span data-stu-id="93015-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="93015-141">Zamiast tego catch i zajmują więcej określony zestaw typów wyjątków lub ponownie zgłosić wyjątek</span><span class="sxs-lookup"><span data-stu-id="93015-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="93015-142">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="93015-142">**Category:** Security</span></span>

<span data-ttu-id="93015-143">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-143">**Severity:** Warning</span></span>

<span data-ttu-id="93015-144">Informacje dodatkowe: [## CA2153: nie Przechwytuj wyjątki uszkodzony](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="93015-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="93015-145">CA2229: Należy zaimplementować konstruktory serializacji</span><span class="sxs-lookup"><span data-stu-id="93015-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="93015-146">Analizatora generuje ostrzeżenie podczas tworzenia typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, ale nie definiuje konstruktora serializacji wymagane.</span><span class="sxs-lookup"><span data-stu-id="93015-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="93015-147">Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="93015-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="93015-148">Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.</span><span class="sxs-lookup"><span data-stu-id="93015-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="93015-149">Konstruktor serializacji ma następującą sygnaturą:</span><span class="sxs-lookup"><span data-stu-id="93015-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="93015-150">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="93015-150">**Category:** Usage</span></span>

<span data-ttu-id="93015-151">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-151">**Severity:** Warning</span></span>

<span data-ttu-id="93015-152">Informacje dodatkowe: [CA2229: zaimplementować konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="93015-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="93015-153">CA2235: Należy oznaczyć wszystkie nieserializowane pola</span><span class="sxs-lookup"><span data-stu-id="93015-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="93015-154">Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="93015-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="93015-155">To pole z jawnie należy oznaczyć <xref:System.NonSerializedAttribute> ustalenie to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="93015-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="93015-156">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="93015-156">**Category:** Usage</span></span>

<span data-ttu-id="93015-157">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-157">**Severity:** Warning</span></span>

<span data-ttu-id="93015-158">Informacje dodatkowe: [CA2235: oznaczyć wszystkie nieserializowane pola](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="93015-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="93015-159">CA2237: Oznacz typy ISerializable z serializacji</span><span class="sxs-lookup"><span data-stu-id="93015-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="93015-160">Aby być rozpoznawane przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone za pomocą <xref:System.SerializableAttribute> atrybutu nawet wtedy, gdy typ używa procedury niestandardowej serializacji zaimplementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="93015-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="93015-161">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="93015-161">**Category:** Usage</span></span>

<span data-ttu-id="93015-162">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-162">**Severity:** Warning</span></span>

<span data-ttu-id="93015-163">Informacje dodatkowe: [CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="93015-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="93015-164">CA3075: Przetwarzanie w kodzie XML definicji DTD niezabezpieczonych</span><span class="sxs-lookup"><span data-stu-id="93015-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="93015-165">Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do zewnętrznej jednostki źródeł, analizator akceptuje niezaufanych argument wejściowy i argument wyjawiać poufnych informacji do osoby atakujące.</span><span class="sxs-lookup"><span data-stu-id="93015-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="93015-166">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="93015-166">**Category:** Security</span></span>

<span data-ttu-id="93015-167">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-167">**Severity:** Warning</span></span>

<span data-ttu-id="93015-168">Informacje dodatkowe: [A3075: niebezpieczne DTD przetwarzania w kodzie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="93015-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="93015-169">CA5350: Nie używaj słabych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="93015-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="93015-170">Algorytmy kryptograficzne zmniejsza się wraz z upływem czasu, jak ataki staną się bardziej zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="93015-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="93015-171">W zależności od typu i stosowania tego algorytmu kryptograficznego, dalsze pogorszenia się jego siły kryptograficznych może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie złamania żadnych cryptosystem na podstawie tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="93015-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="93015-172">Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="93015-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="93015-173">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, np. 512 SHA-2, SHA-2 384 lub 256 SHA-2.</span><span class="sxs-lookup"><span data-stu-id="93015-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="93015-174">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="93015-174">**Category:** Security</span></span>

<span data-ttu-id="93015-175">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-175">**Severity:** Warning</span></span>

<span data-ttu-id="93015-176">Informacje dodatkowe: [CA5350: nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="93015-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="93015-177">CA5351: Nie używaj przerwane algorytmy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="93015-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="93015-178">Istnieje ataku, dzięki czemu można przerwać ten algorytm wykonalne.</span><span class="sxs-lookup"><span data-stu-id="93015-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="93015-179">Dzięki temu osoby atakujące przerwać gwarancje kryptograficznych, który ma na celu zapewnienie.</span><span class="sxs-lookup"><span data-stu-id="93015-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="93015-180">W zależności od typu i stosowania tego algorytmu kryptograficznego to może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia żadnych cryptosystem na podstawie na tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="93015-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="93015-181">Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="93015-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="93015-182">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, takich jak SHA512, SHA384 i SHA256.</span><span class="sxs-lookup"><span data-stu-id="93015-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="93015-183">W przypadku podpisów cyfrowych należy użyć RSA z kluczem o długości większa lub równa 2048 bitów lub ECDSA z kluczem o długości większej niż lub równa 256 bitów.</span><span class="sxs-lookup"><span data-stu-id="93015-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="93015-184">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="93015-184">**Category:** Security</span></span>

<span data-ttu-id="93015-185">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="93015-185">**Severity:** Warning</span></span>

<span data-ttu-id="93015-186">Informacje dodatkowe: [CA5351: nie używaj przerwane algorytmy kryptograficzne](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="93015-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


