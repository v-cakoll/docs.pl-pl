---
title: "Konwencje wielkość liter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1bddb7bb3559e6f39b7884b92f64bee8fbb3510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="capitalization-conventions"></a><span data-ttu-id="e6bdd-102">Konwencje wielkość liter</span><span class="sxs-lookup"><span data-stu-id="e6bdd-102">Capitalization Conventions</span></span>
<span data-ttu-id="e6bdd-103">Wskazówki zawarte w ten rozdział układ prostą metodę przy użyciu przypadek, który po zastosowaniu spójnie upewnij identyfikatory typów, członków i parametry łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="e6bdd-104">Reguły wielkości liter dla identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="e6bdd-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="e6bdd-105">Rozróżnianie słów w identyfikatorze, wielką pierwszą literę każdego wyrazu w identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="e6bdd-106">Nie używaj znaków podkreślenia rozróżnianie słów, lub dla tej sprawy w dowolnym miejscu identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="e6bdd-107">Istnieją dwa sposoby odpowiednie na wielką identyfikatorów, w zależności od użycia identyfikatora:</span><span class="sxs-lookup"><span data-stu-id="e6bdd-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="e6bdd-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="e6bdd-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="e6bdd-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="e6bdd-109">camelCasing</span></span>  
  
 <span data-ttu-id="e6bdd-110">Konwencji PascalCasing używany dla wszystkich identyfikatorów z wyjątkiem nazwy parametrów powoduje rozpoczynanie pierwszy znak każdego wyrazu (w tym akronimów za pośrednictwem dwóch liter o długości), jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="e6bdd-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="e6bdd-111">Szczególnych przypadkach wykonywane akronimów dwuliterowych, w których kapitalizacji zarówno litery, jak pokazano w następującym identyfikatorem:</span><span class="sxs-lookup"><span data-stu-id="e6bdd-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="e6bdd-112">Konwencja camelCasing, używana tylko w przypadku nazw parametrów powoduje rozpoczynanie pierwszy znak każdego wyrazu, z wyjątkiem pierwszej word, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="e6bdd-113">Jako przykład przedstawiono również, akronimów dwuliterowych, rozpoczynające się identyfikatorem liter formatu są małymi literami.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="e6bdd-114">**CZY ✓** Użyj PascalCasing dla wszystkich publicznych nazw elementu członkowskiego, typ i przestrzeń nazw składającą się z wielu wyrazów.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="e6bdd-115">**CZY ✓** camelCasing na użytek nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="e6bdd-116">W poniższej tabeli opisano reguły wielkości liter dla różnych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="e6bdd-117">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e6bdd-117">Identifier</span></span>|<span data-ttu-id="e6bdd-118">Wielkość znaków</span><span class="sxs-lookup"><span data-stu-id="e6bdd-118">Casing</span></span>|<span data-ttu-id="e6bdd-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6bdd-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="e6bdd-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e6bdd-120">Namespace</span></span>|<span data-ttu-id="e6bdd-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="e6bdd-122">Typ</span><span class="sxs-lookup"><span data-stu-id="e6bdd-122">Type</span></span>|<span data-ttu-id="e6bdd-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="e6bdd-124">Interface</span><span class="sxs-lookup"><span data-stu-id="e6bdd-124">Interface</span></span>|<span data-ttu-id="e6bdd-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="e6bdd-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="e6bdd-126">Method</span></span>|<span data-ttu-id="e6bdd-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="e6bdd-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e6bdd-128">Property</span></span>|<span data-ttu-id="e6bdd-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="e6bdd-130">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="e6bdd-130">Event</span></span>|<span data-ttu-id="e6bdd-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="e6bdd-132">Pole</span><span class="sxs-lookup"><span data-stu-id="e6bdd-132">Field</span></span>|<span data-ttu-id="e6bdd-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="e6bdd-134">Wartość wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e6bdd-134">Enum value</span></span>|<span data-ttu-id="e6bdd-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="e6bdd-136">Parametr</span><span class="sxs-lookup"><span data-stu-id="e6bdd-136">Parameter</span></span>|<span data-ttu-id="e6bdd-137">Formatu</span><span class="sxs-lookup"><span data-stu-id="e6bdd-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="e6bdd-138">Zamiany wyrazy złożone i typowe terminy</span><span class="sxs-lookup"><span data-stu-id="e6bdd-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="e6bdd-139">Większość warunki złożone są traktowane jako pojedyncze wyrazy na potrzeby użycia wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="e6bdd-140">**X nie** własne w tzw wyrazy złożone zamknąć formularz.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="e6bdd-141">Są zapisywane jako pojedynczego wyrazu, takie jak punkt końcowy wyrazy złożone.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="e6bdd-142">Na potrzeby wielkości liter dla skrótowców Traktuj wyraz złożony zamknięciu formularza jako pojedynczego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="e6bdd-143">Użyj bieżącego słownika, aby określić, czy wyraz złożony są zapisywane w postaci zamknięte.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="e6bdd-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="e6bdd-144">Pascal</span></span>|<span data-ttu-id="e6bdd-145">Formatu</span><span class="sxs-lookup"><span data-stu-id="e6bdd-145">Camel</span></span>|<span data-ttu-id="e6bdd-146">nie</span><span class="sxs-lookup"><span data-stu-id="e6bdd-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="e6bdd-147">Uwzględniana wielkość liter</span><span class="sxs-lookup"><span data-stu-id="e6bdd-147">Case Sensitivity</span></span>  
 <span data-ttu-id="e6bdd-148">Języki, które można uruchamiać na CLR są nie muszą obsługiwać uwzględnianie wielkości liter, mimo że niektóre czy.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="e6bdd-149">Nawet jeśli język obsługuje tę funkcję, innych języków, które mogą uzyskiwać dostęp do Twojego framework nie.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="e6bdd-150">Wszystkie interfejsy API, które są dostępne z zewnątrz, w związku z tym nie zależą od wielkości liter, samodzielnie, aby rozróżnić dwóch nazw w tym samym kontekście.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="e6bdd-151">**X nie** założono, że wszystkie języki programowania jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="e6bdd-152">Nie są one.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-152">They are not.</span></span> <span data-ttu-id="e6bdd-153">Nazwy nie mogą się różnić w przypadku samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="e6bdd-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="e6bdd-154">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e6bdd-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e6bdd-155">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="e6bdd-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bdd-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6bdd-156">See Also</span></span>  
 [<span data-ttu-id="e6bdd-157">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="e6bdd-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e6bdd-158">Zasady nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e6bdd-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
