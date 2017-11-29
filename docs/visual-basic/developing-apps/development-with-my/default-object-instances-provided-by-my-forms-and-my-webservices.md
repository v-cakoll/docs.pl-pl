---
title: "Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44265c3f6f38a001192a8d92f2fbb6edeaca21cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="0f5fc-102">Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5fc-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="0f5fc-103">[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) i [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) obiektów zapewnienia dostępu do formularzy, źródła danych i usług XML sieci Web używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="0f5fc-104">One to robić przez zapewnienie kolekcji *domyślne wystąpień* każdego z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="0f5fc-105">Domyślne wystąpienia</span><span class="sxs-lookup"><span data-stu-id="0f5fc-105">Default Instances</span></span>  
 <span data-ttu-id="0f5fc-106">Domyślne wystąpienie jest wystąpieniem klasy, która jest dostarczana przez środowisko uruchomieniowe i nie musi być zadeklarowany i wdrożyć przy użyciu `Dim` i `New` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="0f5fc-107">W poniższym przykładzie pokazano sposób może mieć zadeklarowany i utworzone wystąpienie <xref:System.Windows.Forms.Form> klasy o nazwie `Form1`, i jak jesteś teraz można uzyskać domyślnego wystąpienia tego <xref:System.Windows.Forms.Form> klasy za pomocą `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 <span data-ttu-id="0f5fc-108">`My.Forms` Obiektu zwraca kolekcję wystąpień domyślną dla każdego `Form` klasy, który istnieje w projekcie.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="0f5fc-109">Podobnie `My.WebServices` zawiera domyślne wystąpienie klasy serwera proxy dla każdej usługi sieci Web, że utworzono odwołanie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f5fc-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5fc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f5fc-110">See Also</span></span>  
 [<span data-ttu-id="0f5fc-111">My.Forms — obiekt</span><span class="sxs-lookup"><span data-stu-id="0f5fc-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [<span data-ttu-id="0f5fc-112">My.WebServices — obiekt</span><span class="sxs-lookup"><span data-stu-id="0f5fc-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [<span data-ttu-id="0f5fc-113">Jak Moje zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="0f5fc-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
