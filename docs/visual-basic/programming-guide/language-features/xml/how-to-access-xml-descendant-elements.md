---
title: "Porady: dostęp do elementów podrzędnych XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="4d010-102">Porady: dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d010-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="4d010-103">Ten przykład przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML w tym określonej nazwy, są zawarte w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="4d010-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="4d010-104">W szczególności używa `Value` właściwość, aby uzyskać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4d010-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="4d010-105">`name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy o nazwie `name` są zawarte w `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4d010-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="4d010-106">W tym przykładzie również używane `phone` właściwości osi elementu podrzędnego można uzyskać dostępu do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4d010-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d010-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d010-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d010-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4d010-108">Compiling the Code</span></span>  
 <span data-ttu-id="4d010-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4d010-109">This example requires:</span></span>  
  
-   <span data-ttu-id="4d010-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4d010-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d010-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d010-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4d010-112">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="4d010-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="4d010-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="4d010-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="4d010-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d010-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="4d010-115">XML</span><span class="sxs-lookup"><span data-stu-id="4d010-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
