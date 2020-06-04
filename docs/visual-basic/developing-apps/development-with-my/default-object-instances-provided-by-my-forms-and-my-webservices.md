---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 847724450ee2bc8bc591371f71171e8ba4ed9337
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411743"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="5b7ea-102">Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b7ea-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="5b7ea-103">Obiekty [My. Forms](../../language-reference/objects/my-forms-object.md) i [My. WebServices](../../language-reference/objects/my-webservices-object.md) zapewniają dostęp do formularzy, źródeł danych i usług sieci Web XML używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5b7ea-103">The [My.Forms](../../language-reference/objects/my-forms-object.md) and [My.WebServices](../../language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="5b7ea-104">W tym celu należy podać kolekcje *wystąpień domyślnych* każdego z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b7ea-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="5b7ea-105">Wystąpienia domyślne</span><span class="sxs-lookup"><span data-stu-id="5b7ea-105">Default Instances</span></span>  

 <span data-ttu-id="5b7ea-106">Wystąpienie domyślne to wystąpienie klasy dostarczonej przez środowisko uruchomieniowe, które nie musi być zadeklarowane i tworzone przy użyciu `Dim` `New` instrukcji i.</span><span class="sxs-lookup"><span data-stu-id="5b7ea-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="5b7ea-107">Poniższy przykład demonstruje, jak zostało zadeklarowane i wystąpienie wystąpienia <xref:System.Windows.Forms.Form> klasy o nazwie `Form1` i jak teraz można uzyskać domyślne wystąpienie tej <xref:System.Windows.Forms.Form> klasy przez `My.Forms` .</span><span class="sxs-lookup"><span data-stu-id="5b7ea-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="5b7ea-108">`My.Forms`Obiekt zwraca kolekcję wystąpień domyślnych dla każdej `Form` klasy, która istnieje w projekcie.</span><span class="sxs-lookup"><span data-stu-id="5b7ea-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="5b7ea-109">Podobnie, program `My.WebServices` udostępnia domyślne wystąpienie klasy proxy dla każdej usługi sieci Web, w której utworzono odwołanie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5b7ea-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b7ea-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b7ea-110">See also</span></span>

- [<span data-ttu-id="5b7ea-111">My.Forms — Obiekt</span><span class="sxs-lookup"><span data-stu-id="5b7ea-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="5b7ea-112">My.WebServices — Obiekt</span><span class="sxs-lookup"><span data-stu-id="5b7ea-112">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="5b7ea-113">Jak My zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="5b7ea-113">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
