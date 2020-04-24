---
title: Przestrzenie nazw i definicje DTD w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 22762e3a7003d9b28a53c7b500829aaa41924c6d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710599"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="911f4-102">Przestrzenie nazw i definicje DTD w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="911f4-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="911f4-103">Definicje typu dokumentu (DTD) komplikują obsługę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="911f4-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="911f4-104">Na przykład poniższy kod XML zawiera atrybuty domyślne zawierające dwukropki w nazwach.</span><span class="sxs-lookup"><span data-stu-id="911f4-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="911f4-105">Poniżej przedstawiono możliwe rozwiązania, jeśli ta konstrukcja jest dozwolona:</span><span class="sxs-lookup"><span data-stu-id="911f4-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="911f4-106">`x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks musi być rozpoznawalny przy użyciu `xmlns:x` deklaracji przestrzeni nazw, która również musi znajdować się gdzieś w DTD.</span><span class="sxs-lookup"><span data-stu-id="911f4-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="911f4-107">Wystąpił błąd podczas mapowania tego prefiksu na inny element w dokumencie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="911f4-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="911f4-108">`x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks jest zawsze rozpoznawany w kontekście elementów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="911f4-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="911f4-109">Oznacza to, że prefiks może być faktycznie mapowany na różne identyfikatory Uniform Resource Identifier (URI) obszaru nazw, w zależności od zakresu przestrzeni `item` nazw, w którym jest wyświetlany element.</span><span class="sxs-lookup"><span data-stu-id="911f4-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="911f4-110">To zachowanie jest bardziej przewidywalne niż rozdzielczość podaną we wcześniejszym punktorze, ale ma inne skomplikowane konsekwencje, ponieważ wymaga podania atrybutów domyślnych.</span><span class="sxs-lookup"><span data-stu-id="911f4-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="911f4-111">Dwukropek jest ignorowany, ponieważ znajduje się w DTD, a nazwa atrybutu to `x:y`, brak prefiksu i brak identyfikatora URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="911f4-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="911f4-112">Dwukropek w atrybucie domyślnym zgłasza wyjątek, co oznacza, że dwukropek w nazwach w DTD nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="911f4-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="911f4-113">Powoduje to przewidywalną zachowanie, ale oznacza, że nie można załadować wielu organizacja World Wide Web Consortium (W3C) opublikowanych elementów DTD.</span><span class="sxs-lookup"><span data-stu-id="911f4-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="911f4-114">Gdy użytkownik zażąda walidacji DTD, obsługa przestrzeni nazw dla całego dokumentu jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="911f4-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="911f4-115">Dzięki temu można załadować definicje W3C i uzyskać przewidywalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="911f4-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="911f4-116">KOD XML w Microsoft .NET Framework implementuje drugą opcję maksymalnej zgodności W3C.</span><span class="sxs-lookup"><span data-stu-id="911f4-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911f4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="911f4-117">See also</span></span>

- [<span data-ttu-id="911f4-118">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="911f4-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
