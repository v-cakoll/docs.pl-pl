---
title: Żądania połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29a3254bb5ccfe422a1c2d7d156975c0887d9273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="link-demands"></a><span data-ttu-id="19aa2-102">Żądania połączeń</span><span class="sxs-lookup"><span data-stu-id="19aa2-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="19aa2-103">Żądanie łącza powoduje, że kontrola zabezpieczeń podczas kompilacji w czasie i sprawdza tylko bezpośredniego wywołującego zestawu kodu.</span><span class="sxs-lookup"><span data-stu-id="19aa2-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="19aa2-104">Łączenie występuje, gdy kod jest powiązany z odwołania typu, łącznie z odwołania do wskaźnika funkcji i wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="19aa2-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="19aa2-105">Jeśli zestaw wywołujący nie ma wystarczających uprawnień do połączenia w kodzie, łącze jest niedozwolone, a wyjątek czasu wykonywania jest zgłaszany, gdy kod jest załadowany i uruchom.</span><span class="sxs-lookup"><span data-stu-id="19aa2-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="19aa2-106">Linkdemand może zostać przesłonięta w klasach, które dziedziczą z kodu.</span><span class="sxs-lookup"><span data-stu-id="19aa2-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="19aa2-107">Zanotuj przeszukiwania pełnego stosu nie jest wykonywane z tym typem żądanie i czy kod jest nadal podatne na ataki zapewnienia.</span><span class="sxs-lookup"><span data-stu-id="19aa2-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="19aa2-108">Na przykład jeśli metoda w zestawie A jest chroniony przez żądanie łącza, bezpośredniego obiektu wywołującego w zestawie B jest obliczane na podstawie uprawnień zestawu B.  Jednak linkdemand nie będą używać metody w zestawie C pośrednio wywołuje metody w zestawie przy użyciu metody w zestawie B. Żądanie łącze Określa, że tylko uprawnienia bezpośrednich wywołań w bezpośredniego wywołującego zestawu musi mieć do połączenia w kodzie.</span><span class="sxs-lookup"><span data-stu-id="19aa2-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="19aa2-109">Nie określono uprawnień wszystkim zainteresowanym niezbędne do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="19aa2-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="19aa2-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, I <xref:System.Security.CodeAccessPermission.PermitOnly%2A> Modyfikatory przeszukiwania stosu nie wpływają na obliczanie linkdemand.</span><span class="sxs-lookup"><span data-stu-id="19aa2-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="19aa2-111">Ponieważ linkdemand nie wykonuj przeszukiwania stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na linkdemand.</span><span class="sxs-lookup"><span data-stu-id="19aa2-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="19aa2-112">Jeśli metoda chroniony przez żądanie łącza jest dostępny za pośrednictwem [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md), żądanie łącza sprawdza bezpośredniego obiektu wywołującego kodu dostępne za pośrednictwem odbicia.</span><span class="sxs-lookup"><span data-stu-id="19aa2-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="19aa2-113">Dotyczy to zarówno w przypadku metody odnajdywania, jak i wywołanie metody wykonywane przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="19aa2-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="19aa2-114">Na przykład kodu wykorzystuje odbicia do zwrócenia <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę chroniony przez żądanie łącza i który następnie przekazuje **MethodInfo** obiekt inny kod używa obiektu można wywołać metody oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="19aa2-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="19aa2-115">W takim przypadku sprawdź żądanie łącze występuje dwa razy: raz dla kodu, która zwraca **MethodInfo** obiekt i kod, który wywołuje ona — jeden raz.</span><span class="sxs-lookup"><span data-stu-id="19aa2-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19aa2-116">Żądanie łącza wykonane w konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżka wykonywania kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19aa2-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="19aa2-117">W związku z tym kiedy żądanie łącza jest stosowany dla całej klasy, nie chroni dostęp do konstruktora statycznego chociaż chronić rest klasy.</span><span class="sxs-lookup"><span data-stu-id="19aa2-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="19aa2-118">Poniższy fragment kodu deklaratywnie określa żadnego kodu połączenie `ReadData` metoda musi mieć `CustomPermission` uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="19aa2-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="19aa2-119">To uprawnienie jest hipotetyczny uprawnień niestandardowych i nie istnieje w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19aa2-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="19aa2-120">Żądanie zostało utworzone przez przekazanie **SecurityAction.LinkDemand** flaga `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="19aa2-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="19aa2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19aa2-121">See Also</span></span>  
 [<span data-ttu-id="19aa2-122">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19aa2-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="19aa2-123">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="19aa2-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
