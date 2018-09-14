---
title: Przestrzenie nazw i definicje DTD w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569765"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="4ea71-102">Przestrzenie nazw i definicje DTD w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="4ea71-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="4ea71-103">Obsługa complicate przestrzeni nazw definicje (pliki DTD) typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4ea71-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="4ea71-104">Na przykład następujący kod XML zawiera atrybuty domyślne zawierające dwukropki w nazwach.</span><span class="sxs-lookup"><span data-stu-id="4ea71-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="4ea71-105">Poniżej przedstawiono możliwe rozwiązania, jeśli ta konstrukcja jest dozwolony:</span><span class="sxs-lookup"><span data-stu-id="4ea71-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="4ea71-106">`x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks musi być rozpoznawalna przy użyciu `xmlns:x` deklaracji przestrzeni nazw musi również istnieć gdzieś w DTD.</span><span class="sxs-lookup"><span data-stu-id="4ea71-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="4ea71-107">Jest to błąd, aby zamapować tego prefiksu na coś innego w dokumencie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ea71-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="4ea71-108">`x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks jest zawsze rozwiązane w kontekście elementów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ea71-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="4ea71-109">Oznacza to, że do innej przestrzeni nazw Uniform Resource Identifier (URI), w zależności od zakresu przestrzeni nazw, w którym faktycznie zamapować prefiksu `item` element jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="4ea71-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="4ea71-110">To zachowanie jest bardziej przewidywalna od rozdzielczości w starszych punktor, ale ma inne zagadnienia skomplikowane, ponieważ wymaga, aby być zmaterializowany atrybutów domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4ea71-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="4ea71-111">Dwukropek jest ignorowana, ponieważ znajduje się w DTD, a nazwa atrybutu jest `x:y`, żadnego prefiksu i obszaru nazw URI.</span><span class="sxs-lookup"><span data-stu-id="4ea71-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="4ea71-112">Dwukropek w atrybucie domyślne zgłasza wyjątek, informujący o tym w dwukropki w nazwach w DTD są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4ea71-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="4ea71-113">Skutkuje to zachowanie przewidywalne, ale nie można załadować wiele World Wide Web Consortium (W3C) oznacza, że publikowane definicje DTD.</span><span class="sxs-lookup"><span data-stu-id="4ea71-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="4ea71-114">Gdy użytkownik zażąda weryfikacji DTD, obsługa przestrzeni nazw dla całego dokumentu jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="4ea71-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="4ea71-115">Dzięki temu można załadować definicji DTD W3C i powoduje zachowanie przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="4ea71-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="4ea71-116">Kod XML w Microsoft .NET Framework implementuje drugą opcją Maksymalna zgodność W3C.</span><span class="sxs-lookup"><span data-stu-id="4ea71-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea71-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ea71-117">See also</span></span>

- [<span data-ttu-id="4ea71-118">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="4ea71-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
