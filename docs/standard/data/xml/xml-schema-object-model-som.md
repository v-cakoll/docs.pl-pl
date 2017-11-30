---
title: Model obiektu schematu XML (SOM)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 44ce1337e347020926fe2dee29d70fe226ad087a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="8c09e-102">Model obiektu schematu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="8c09e-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="8c09e-103">Schemat XML jest zaawansowaną i złożonych narzędzie do tworzenia i weryfikowania struktury w dokumentach XML zgodne.</span><span class="sxs-lookup"><span data-stu-id="8c09e-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="8c09e-104">Podobnie jak danych modelowania relacyjnej bazy danych, schemat udostępnia sposób definiowania struktury dokumentów XML, określając elementy, które mogą być używane w dokumentów, a także struktury i typy, które tych elementów należy wykonać, aby obowiązywać określona t określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="8c09e-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="8c09e-105">Model obiektu schematu (SOM) zawiera zestaw klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, która pozwala na odczyt z pliku schematu lub programowane tworzenie schematu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c09e-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="8c09e-106">Schemat następnie można przejść wzdłuż, edytowania, kompilacji, sprawdzania poprawności lub zapisywane w pliku.</span><span class="sxs-lookup"><span data-stu-id="8c09e-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c09e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8c09e-107">In This Section</span></span>  
 [<span data-ttu-id="8c09e-108">Omówienie modelu obiektu schematu XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="8c09e-109">Opisuje modelu obiektu schematu (SOM) i funkcje i klasy, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="8c09e-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="8c09e-110">Odczytywanie i zapisywanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="8c09e-111">Opisuje sposób odczytywania i zapisywania schematów XML z plików lub innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="8c09e-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="8c09e-112">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="8c09e-113">Informacje dotyczące używania klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw do tworzenia XML schematów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c09e-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="8c09e-114">Przechodzenie przez schematy XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="8c09e-115">Opisuje sposób przenoszenia schematu XML dostępu do elementy, atrybuty i przechowywane w SOM. typów</span><span class="sxs-lookup"><span data-stu-id="8c09e-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="8c09e-116">Edytowanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="8c09e-117">Opisuje sposób edytowania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="8c09e-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="8c09e-118">W tym lub importowanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="8c09e-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="8c09e-119">Opisuje sposób uwzględniać lub importować inne schematy XML uzupełnienie Struktura schematu, która obejmuje lub importowane.</span><span class="sxs-lookup"><span data-stu-id="8c09e-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
