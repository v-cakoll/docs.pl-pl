---
title: Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839369"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="9ddd8-102">Domyślne wystąpienia obiektu zapewniane przez My.Forms i My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ddd8-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="9ddd8-103">[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) i [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) obiekty zapewniają dostęp do formularzy, źródła danych i usług sieci Web XML używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="9ddd8-104">Mogą to zrobić, podając kolekcji *domyślne wystąpień* każdego z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="9ddd8-105">Domyślne wystąpienia</span><span class="sxs-lookup"><span data-stu-id="9ddd8-105">Default Instances</span></span>  
 <span data-ttu-id="9ddd8-106">Domyślne wystąpienie jest wystąpieniem klasy, które są dostarczane przez środowisko uruchomieniowe, a musi być zadeklarowana i tworzone przy użyciu `Dim` i `New` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="9ddd8-107">W poniższym przykładzie pokazano, jak może mieć zadeklarowana i utworzone wystąpienie <xref:System.Windows.Forms.Form> klasę o nazwie `Form1`, jak automatycznie zalogujesz się można uzyskać domyślnego wystąpienia tego <xref:System.Windows.Forms.Form> klasy za pomocą `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="9ddd8-108">`My.Forms` Obiektu zwraca kolekcję wystąpień domyślną dla każdego `Form` klasę, która istnieje w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="9ddd8-109">Podobnie `My.WebServices` zapewnia domyślne wystąpienie klasy proxy dla każdej usługi w sieci Web, że utworzono odwołanie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ddd8-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ddd8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ddd8-110">See also</span></span>

- [<span data-ttu-id="9ddd8-111">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="9ddd8-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="9ddd8-112">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="9ddd8-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="9ddd8-113">Jak My zależy od typu projektu</span><span class="sxs-lookup"><span data-stu-id="9ddd8-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
