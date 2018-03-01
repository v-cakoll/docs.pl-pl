---
title: Praca z obiektami dynamicznymi (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="fc143-102">Praca z obiektami dynamicznymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc143-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="fc143-103">Obiekty dynamiczne Podaj inny sposób inny niż `Object` typ późne wiązanie z obiektu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc143-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="fc143-104">Obiekt dynamiczny uwidacznia elementy członkowskie, takie jak właściwości i metody w czasie wykonywania za pomocą dynamicznej interfejsów, które są zdefiniowane w <xref:System.Dynamic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc143-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="fc143-105">Można użyć klasy w <xref:System.Dynamic> przestrzeni nazw do tworzenia obiektów, które współpracują z struktury danych, które nie są zgodne, statyczne typ lub format.</span><span class="sxs-lookup"><span data-stu-id="fc143-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="fc143-106">Umożliwia także obiekty dynamiczne, które są zdefiniowane w dynamicznej języków, takich jak IronPython i IronRuby.</span><span class="sxs-lookup"><span data-stu-id="fc143-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="fc143-107">Przykłady, które pokazują, jak utworzyć obiekty dynamiczne lub użyć obiekt dynamiczny zdefiniowany w języku dynamicznej, zobacz [wskazówki: tworzenie i użycie obiekty dynamiczne](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, lub <xref:System.Dynamic.ExpandoObject>.</span><span class="sxs-lookup"><span data-stu-id="fc143-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="fc143-108">wiąże obiektów ze środowiska uruchomieniowego języka dynamicznego i dynamiczne języków, takich jak IronPython i IronRuby przy użyciu <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fc143-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="fc143-109">Przykłady klas implementujących `IDynamicMetaObjectProvider` interfejsu są <xref:System.Dynamic.DynamicObject> i <xref:System.Dynamic.ExpandoObject> klasy.</span><span class="sxs-lookup"><span data-stu-id="fc143-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="fc143-110">Jeśli wywołanie późnym wiązaniem dotyczące obiekt, który implementuje `IDynamicMetaObjectProvider` interfejsu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wiąże obiekt dynamiczny przy użyciu tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fc143-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="fc143-111">Jeśli wykonano wywołanie z późnym wiązaniem do obiektu, który nie implementuje `IDynamicMetaObjectProvider` interfejsu, lub, jeśli wywołanie `IDynamicMetaObjectProvider` interfejsu kończy się niepowodzeniem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wiąże obiekt przy użyciu możliwości późne wiązanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="fc143-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc143-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc143-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="fc143-113">Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie</span><span class="sxs-lookup"><span data-stu-id="fc143-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="fc143-114">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="fc143-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
