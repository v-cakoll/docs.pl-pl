---
title: "Analizatory zabezpieczeń .NET - .NET"
description: "Używanie analizatorów zabezpieczeń .NET w pakiecie programu .NET Framework analizatorów znaleźć i zagrożenia bezpieczeństwa"
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 06a387d72d06609182c8894dd874b241a5d7b69c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="16291-104">Analizator Framework .NET</span><span class="sxs-lookup"><span data-stu-id="16291-104">The .NET Framework Analyzer</span></span>

<span data-ttu-id="16291-105">Analizator Framework .NET umożliwia znaleźć potencjalnych problemów w kodzie aplikacji opartych na programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16291-105">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="16291-106">Ta analizator znajduje potencjalne problemy, a także sugeruje rozwiązania ich.</span><span class="sxs-lookup"><span data-stu-id="16291-106">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="16291-107">Analizatora interaktywnie działa w programie Visual Studio podczas pisania kodu lub w ramach elementu konfiguracji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="16291-107">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="16291-108">Przy projektowaniu, należy dodać analizatora możliwie jak najszybciej do projektu.</span><span class="sxs-lookup"><span data-stu-id="16291-108">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="16291-109">Wcześniej odnaleźć dotyczących potencjalnych problemów w kodzie, tym łatwiej są Aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="16291-109">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="16291-110">Jednak można go dodać w dowolnym momencie w cyklu programowania.</span><span class="sxs-lookup"><span data-stu-id="16291-110">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="16291-111">Jego znajduje problemy z istniejącego kodu i ostrzeganie o nowe problemy, jak zachować opracowywania.</span><span class="sxs-lookup"><span data-stu-id="16291-111">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="16291-112">Instalowanie i konfigurowanie analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="16291-112">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="16291-113">Analizatory zabezpieczeń .NET musi być zainstalowany jako pakietu NuGet, na każdy projekt, gdzie chcesz je uruchomić.</span><span class="sxs-lookup"><span data-stu-id="16291-113">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="16291-114">Tylko jeden deweloper musi je dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="16291-114">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="16291-115">Pakiet Analizator jest zależności projektu i zostanie uruchomiony na maszynie Każdy deweloper, gdy ma ona zaktualizowane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="16291-115">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="16291-116">Analizator Framework .NET jest dostarczany w [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="16291-116">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="16291-117">Ten pakiet zawiera określone analizatorów programu .NET Framework, w tym analizatorów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="16291-117">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="16291-118">W większości przypadków należy [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="16291-118">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="16291-119">Pakiet agregacji FxCopAnalyzers zawiera analizatorów framework zawarte w pakiecie Framework.Analyzers, jak również analizatory następujące:</span><span class="sxs-lookup"><span data-stu-id="16291-119">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="16291-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API architektury .NET</span><span class="sxs-lookup"><span data-stu-id="16291-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="16291-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): zawiera analizatorów określonych do interfejsów API architektury .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16291-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="16291-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): znajdują się wskazówki dotyczące tekstu jako kod, w tym komentarzy.</span><span class="sxs-lookup"><span data-stu-id="16291-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="16291-123">Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz pozycję "Zarządzaj zależności".</span><span class="sxs-lookup"><span data-stu-id="16291-123">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="16291-124">W Eksploratorze NuGet, wyszukaj "NetFramework analizator", lub jeśli wolisz "Fx Cop analizator".</span><span class="sxs-lookup"><span data-stu-id="16291-124">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="16291-125">Zainstaluj najnowszą wersję stabilna ze wszystkich projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="16291-125">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="16291-126">Za pomocą analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="16291-126">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="16291-127">Po zainstalowaniu pakietu NuGet, Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="16291-127">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="16291-128">Analizatora będzie Zgłoś wszelkie problemy, które klient zlokalizuje baza kodu.</span><span class="sxs-lookup"><span data-stu-id="16291-128">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="16291-129">Problemy są raportowane klientowi jako ostrzeżenia w oknie Lista błędów w usłudze Visual Studio, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="16291-129">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemy zgłoszone przez analizator framework](./media/framework-analyzers-2.png)

<span data-ttu-id="16291-131">Podczas pisania kodu, zobaczysz zygzaki poniżej wszelkie potencjalne problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="16291-131">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="16291-132">Umieść kursor nad jakikolwiek problem, i zobaczyć szczegółowe informacje o problemie i sugestie dotyczące wszystkie możliwe rozwiązanie, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="16291-132">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interakcyjny raport problemów wykrytych przez analizatora framework](./media/framework-analyzers-1.png)

<span data-ttu-id="16291-134">Analizatory badanie kodu w rozwiązaniu i udostępnić listę ostrzeżeń dla każdego z tych problemów:</span><span class="sxs-lookup"><span data-stu-id="16291-134">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="16291-135">CA1058: Typy nie powinny rozszerzać pewnych typów bazowych</span><span class="sxs-lookup"><span data-stu-id="16291-135">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="16291-136">Istnieje niewielka liczba typów w programie .NET Framework należy nie pochodzi od bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="16291-136">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="16291-137">**Kategoria:** projektu</span><span class="sxs-lookup"><span data-stu-id="16291-137">**Category:** Design</span></span>

<span data-ttu-id="16291-138">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-138">**Severity:** Warning</span></span>

<span data-ttu-id="16291-139">Informacje dodatkowe: [CA:1058: typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="16291-139">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="16291-140">CA2153: Nie Przechwytuj wyjątki uszkodzony</span><span class="sxs-lookup"><span data-stu-id="16291-140">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="16291-141">Połowowe wyjątki uszkodzony można zamaskować błędy (np. naruszenia zasad dostępu), co w stanie niespójnym wykonywania lub ułatwieniu osobom atakującym naruszyć bezpieczeństwo systemu.</span><span class="sxs-lookup"><span data-stu-id="16291-141">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="16291-142">Zamiast tego catch i zajmują więcej określony zestaw typów wyjątków lub ponownie zgłosić wyjątek</span><span class="sxs-lookup"><span data-stu-id="16291-142">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="16291-143">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="16291-143">**Category:** Security</span></span>

<span data-ttu-id="16291-144">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-144">**Severity:** Warning</span></span>

<span data-ttu-id="16291-145">Informacje dodatkowe: [## CA2153: nie Przechwytuj wyjątki uszkodzony](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="16291-145">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="16291-146">CA2229: Należy zaimplementować konstruktory serializacji</span><span class="sxs-lookup"><span data-stu-id="16291-146">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="16291-147">Analizatora generuje ostrzeżenie podczas tworzenia typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, ale nie definiuje konstruktora serializacji wymagane.</span><span class="sxs-lookup"><span data-stu-id="16291-147">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="16291-148">Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="16291-148">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="16291-149">Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.</span><span class="sxs-lookup"><span data-stu-id="16291-149">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="16291-150">Konstruktor serializacji ma następującą sygnaturą:</span><span class="sxs-lookup"><span data-stu-id="16291-150">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="16291-151">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="16291-151">**Category:** Usage</span></span>

<span data-ttu-id="16291-152">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-152">**Severity:** Warning</span></span>

<span data-ttu-id="16291-153">Informacje dodatkowe: [CA2229: zaimplementować konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="16291-153">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="16291-154">CA2235: Należy oznaczyć wszystkie nieserializowane pola</span><span class="sxs-lookup"><span data-stu-id="16291-154">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="16291-155">Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="16291-155">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="16291-156">To pole z jawnie należy oznaczyć <xref:System.NonSerializedAttribute> ustalenie to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="16291-156">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="16291-157">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="16291-157">**Category:** Usage</span></span>

<span data-ttu-id="16291-158">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-158">**Severity:** Warning</span></span>

<span data-ttu-id="16291-159">Informacje dodatkowe: [CA2235: oznaczyć wszystkie nieserializowane pola](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="16291-159">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="16291-160">CA2237: Oznacz typy ISerializable z serializacji</span><span class="sxs-lookup"><span data-stu-id="16291-160">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="16291-161">Aby być rozpoznawane przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone za pomocą <xref:System.SerializableAttribute> atrybutu nawet wtedy, gdy typ używa procedury niestandardowej serializacji zaimplementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="16291-161">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="16291-162">**Kategoria:** użycia</span><span class="sxs-lookup"><span data-stu-id="16291-162">**Category:** Usage</span></span>

<span data-ttu-id="16291-163">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-163">**Severity:** Warning</span></span>

<span data-ttu-id="16291-164">Informacje dodatkowe: [CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="16291-164">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="16291-165">CA3075: Przetwarzanie w kodzie XML definicji DTD niezabezpieczonych</span><span class="sxs-lookup"><span data-stu-id="16291-165">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="16291-166">Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do zewnętrznej jednostki źródeł, analizator akceptuje niezaufanych argument wejściowy i argument wyjawiać poufnych informacji do osoby atakujące.</span><span class="sxs-lookup"><span data-stu-id="16291-166">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="16291-167">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="16291-167">**Category:** Security</span></span>

<span data-ttu-id="16291-168">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-168">**Severity:** Warning</span></span>

<span data-ttu-id="16291-169">Informacje dodatkowe: [A3075: niebezpieczne DTD przetwarzania w kodzie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="16291-169">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="16291-170">CA5350: Nie używaj słabych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="16291-170">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="16291-171">Algorytmy kryptograficzne zmniejsza się wraz z upływem czasu, jak ataki staną się bardziej zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="16291-171">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="16291-172">W zależności od typu i stosowania tego algorytmu kryptograficznego, dalsze pogorszenia się jego siły kryptograficznych może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie złamania żadnych cryptosystem na podstawie tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="16291-172">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="16291-173">Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="16291-173">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="16291-174">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, np. 512 SHA-2, SHA-2 384 lub 256 SHA-2.</span><span class="sxs-lookup"><span data-stu-id="16291-174">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="16291-175">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="16291-175">**Category:** Security</span></span>

<span data-ttu-id="16291-176">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-176">**Severity:** Warning</span></span>

<span data-ttu-id="16291-177">Informacje dodatkowe: [CA5350: nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="16291-177">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="16291-178">CA5351: Nie używaj przerwane algorytmy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="16291-178">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="16291-179">Istnieje ataku, dzięki czemu można przerwać ten algorytm wykonalne.</span><span class="sxs-lookup"><span data-stu-id="16291-179">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="16291-180">Dzięki temu osoby atakujące przerwać gwarancje kryptograficznych, który ma na celu zapewnienie.</span><span class="sxs-lookup"><span data-stu-id="16291-180">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="16291-181">W zależności od typu i stosowania tego algorytmu kryptograficznego to może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia żadnych cryptosystem na podstawie na tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="16291-181">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="16291-182">Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="16291-182">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="16291-183">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, takich jak SHA512, SHA384 i SHA256.</span><span class="sxs-lookup"><span data-stu-id="16291-183">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="16291-184">W przypadku podpisów cyfrowych należy użyć RSA z kluczem o długości większa lub równa 2048 bitów lub ECDSA z kluczem o długości większej niż lub równa 256 bitów.</span><span class="sxs-lookup"><span data-stu-id="16291-184">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="16291-185">**Kategoria:** zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="16291-185">**Category:** Security</span></span>

<span data-ttu-id="16291-186">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="16291-186">**Severity:** Warning</span></span>

<span data-ttu-id="16291-187">Informacje dodatkowe: [CA5351: nie używaj przerwane algorytmy kryptograficzne](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="16291-187">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


