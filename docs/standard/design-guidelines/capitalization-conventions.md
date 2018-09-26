---
title: Konwencje dotyczące wielkości liter
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089026"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="4abc3-102">Konwencje dotyczące wielkości liter</span><span class="sxs-lookup"><span data-stu-id="4abc3-102">Capitalization Conventions</span></span>
<span data-ttu-id="4abc3-103">Wskazówki zawarte w tym rozdziale układ w prosty sposób za pomocą sprawa, po zastosowaniu spójnie upewnij identyfikatory dla typów, elementów członkowskich i parametrów, łatwe do odczytania.</span><span class="sxs-lookup"><span data-stu-id="4abc3-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="4abc3-104">Reguły wielkości liter dla identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="4abc3-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="4abc3-105">Do odróżnienia słów w identyfikatorze, wielką pierwszą literę każdego wyrazu w identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="4abc3-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="4abc3-106">Nie należy używać znaków podkreślenia do odróżnienia wyrazów, lub dla tej sprawy w dowolnym miejscu w identyfikatorach.</span><span class="sxs-lookup"><span data-stu-id="4abc3-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="4abc3-107">Istnieją dwa sposoby odpowiednie na wielką identyfikatorów, w zależności od tego, użyj identyfikatora:</span><span class="sxs-lookup"><span data-stu-id="4abc3-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="4abc3-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="4abc3-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="4abc3-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="4abc3-109">camelCasing</span></span>  
  
 <span data-ttu-id="4abc3-110">Konwencja PascalCasing, umożliwiający wszystkie identyfikatory z wyjątkiem nazw parametrów powoduje rozpoczynanie pierwszego znaku wystąpień poszczególnych wyrazów (w tym akronimów za pośrednictwem dwóch liter o długości), jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="4abc3-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="4abc3-111">Przypadek specjalny wysłaniu akronimów dwuliterowych, w których oba litery pod tym, jak pokazano w następującym identyfikatorem:</span><span class="sxs-lookup"><span data-stu-id="4abc3-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="4abc3-112">Konwencja camelCasing, używana tylko w przypadku nazwy parametrów powoduje rozpoczynanie pierwszym znakiem każdego wyrazu, z wyjątkiem pierwszy wyraz, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="4abc3-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="4abc3-113">W przykładzie pokazano również, skrótów dwuliterowych, które zaczynają się identyfikatorem formacie camelcase są zarówno małe litery.</span><span class="sxs-lookup"><span data-stu-id="4abc3-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="4abc3-114">**✓ DO** Użyj PascalCasing dla wszystkich publicznych nazw elementu członkowskiego, typ i przestrzeń nazw składającą się z wielu wyrazów.</span><span class="sxs-lookup"><span data-stu-id="4abc3-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="4abc3-115">**✓ DO** camelCasing na użytek nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="4abc3-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="4abc3-116">W poniższej tabeli opisano reguły wielkości liter dla różnych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="4abc3-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="4abc3-117">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="4abc3-117">Identifier</span></span>|<span data-ttu-id="4abc3-118">Wielkość znaków</span><span class="sxs-lookup"><span data-stu-id="4abc3-118">Casing</span></span>|<span data-ttu-id="4abc3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="4abc3-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="4abc3-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4abc3-120">Namespace</span></span>|<span data-ttu-id="4abc3-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="4abc3-122">Typ</span><span class="sxs-lookup"><span data-stu-id="4abc3-122">Type</span></span>|<span data-ttu-id="4abc3-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="4abc3-124">Interface</span><span class="sxs-lookup"><span data-stu-id="4abc3-124">Interface</span></span>|<span data-ttu-id="4abc3-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="4abc3-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="4abc3-126">Method</span></span>|<span data-ttu-id="4abc3-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="4abc3-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4abc3-128">Property</span></span>|<span data-ttu-id="4abc3-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="4abc3-130">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4abc3-130">Event</span></span>|<span data-ttu-id="4abc3-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="4abc3-132">Pole</span><span class="sxs-lookup"><span data-stu-id="4abc3-132">Field</span></span>|<span data-ttu-id="4abc3-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="4abc3-134">Wartość wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4abc3-134">Enum value</span></span>|<span data-ttu-id="4abc3-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="4abc3-136">Parametr</span><span class="sxs-lookup"><span data-stu-id="4abc3-136">Parameter</span></span>|<span data-ttu-id="4abc3-137">Mechanizm stosowania formatu</span><span class="sxs-lookup"><span data-stu-id="4abc3-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="4abc3-138">Wykorzystując wyrazy złożone i typowe terminy</span><span class="sxs-lookup"><span data-stu-id="4abc3-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="4abc3-139">Większość warunki złożone są traktowane jako pojedynczego słowa do celów wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="4abc3-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="4abc3-140">**X DO NOT** własne w tzw wyrazy złożone zamknąć formularz.</span><span class="sxs-lookup"><span data-stu-id="4abc3-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="4abc3-141">Te są zapisywane jako jednego wyrazu, takie jak punkt końcowy wyrazy złożone.</span><span class="sxs-lookup"><span data-stu-id="4abc3-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="4abc3-142">Na potrzeby liter dla skrótowców należy traktować wyraz złożony zamknięte formularza jako pojedynczego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="4abc3-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="4abc3-143">Użyj bieżącym słowniku, aby określić, wyraz złożony zostanie zapisane w postaci zamknięte.</span><span class="sxs-lookup"><span data-stu-id="4abc3-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="4abc3-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="4abc3-144">Pascal</span></span>|<span data-ttu-id="4abc3-145">Mechanizm stosowania formatu</span><span class="sxs-lookup"><span data-stu-id="4abc3-145">Camel</span></span>|<span data-ttu-id="4abc3-146">nie</span><span class="sxs-lookup"><span data-stu-id="4abc3-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="4abc3-147">Rozróżnianie wielkości liter</span><span class="sxs-lookup"><span data-stu-id="4abc3-147">Case Sensitivity</span></span>  
 <span data-ttu-id="4abc3-148">Języki, które można uruchamiać na środowisko CLR nie są wymagane do obsługi uwzględnianie wielkości liter, mimo że niektóre zrobić.</span><span class="sxs-lookup"><span data-stu-id="4abc3-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="4abc3-149">Nawet wtedy, gdy język obsługuje tę funkcję, nie są inne języki, które mogą uzyskiwać dostęp do swojej platformy.</span><span class="sxs-lookup"><span data-stu-id="4abc3-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="4abc3-150">Wszystkie interfejsy API, które są dostępne z zewnątrz, dlatego nie można polegać na przypadek samodzielnie, aby rozróżnić dwóch nazw, w tym samym kontekście.</span><span class="sxs-lookup"><span data-stu-id="4abc3-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="4abc3-151">**X DO NOT** założono, że wszystkie języki programowania jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="4abc3-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="4abc3-152">Nie są one.</span><span class="sxs-lookup"><span data-stu-id="4abc3-152">They are not.</span></span> <span data-ttu-id="4abc3-153">Nazwy nie mogą się różnić w przypadku autonomicznej.</span><span class="sxs-lookup"><span data-stu-id="4abc3-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="4abc3-154">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="4abc3-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4abc3-155">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="4abc3-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abc3-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4abc3-156">See also</span></span>

- [<span data-ttu-id="4abc3-157">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="4abc3-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="4abc3-158">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="4abc3-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
