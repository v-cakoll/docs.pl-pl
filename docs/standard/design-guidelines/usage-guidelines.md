---
title: "Wskazówki dotyczące użycia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df0d1c5f8bff9d4cb546378f281a44c696246553
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="usage-guidelines"></a><span data-ttu-id="abd29-102">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="abd29-102">Usage Guidelines</span></span>
<span data-ttu-id="abd29-103">Ta sekcja zawiera wskazówki dotyczące używania popularne typy w publicznie interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="abd29-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="abd29-104">Dotyczy on bezpośredniego użycia wbudowanych typów Framework (np. serializacji atrybutów) i przeładowanie operatorów wspólnej.</span><span class="sxs-lookup"><span data-stu-id="abd29-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="abd29-105"><xref:System.IDisposable?displayProperty=nameWithType> Interfejsu nie jest uwzględnione w tej sekcji, ale została szczegółowo opisana w [wzorzec Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="abd29-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd29-106">Wskazówki i dodatkowe informacje o innych typowe wbudowanych typów .NET Framework, zobacz Tematy odwołania dla następujących: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="abd29-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abd29-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="abd29-107">In This Section</span></span>  
 [<span data-ttu-id="abd29-108">Tablice</span><span class="sxs-lookup"><span data-stu-id="abd29-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="abd29-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="abd29-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="abd29-110">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="abd29-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="abd29-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="abd29-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="abd29-112">Użycie zestawów System.Xml</span><span class="sxs-lookup"><span data-stu-id="abd29-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="abd29-113">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="abd29-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="abd29-114">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="abd29-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="abd29-115">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="abd29-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd29-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abd29-116">See Also</span></span>  
 [<span data-ttu-id="abd29-117">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="abd29-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
