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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181171"
---
# <a name="link-demands"></a><span data-ttu-id="3c615-102">Żądania połączeń</span><span class="sxs-lookup"><span data-stu-id="3c615-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="3c615-103">Żądanie łącza powoduje sprawdzanie zabezpieczeń podczas kompilacji just-in-time i sprawdza tylko natychmiastowe wywołanie zestawu kodu.</span><span class="sxs-lookup"><span data-stu-id="3c615-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="3c615-104">Łączenie występuje, gdy kod jest powiązany z odwołaniem do typu, w tym odwołania do wskaźnika funkcji i wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3c615-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="3c615-105">Jeśli zestaw wywołujący nie ma wystarczających uprawnień do łącza do kodu, łącze jest niedozwolone i wyjątek środowiska uruchomieniowego jest zgłaszany, gdy kod jest ładowany i uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="3c615-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="3c615-106">Żądania łącza można zastąpić w klasach, które dziedziczą z kodu.</span><span class="sxs-lookup"><span data-stu-id="3c615-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="3c615-107">Należy zauważyć, że pełny spacer stosu nie jest wykonywane z tego typu popytu i że kod jest nadal podatne na ataki zwabiania.</span><span class="sxs-lookup"><span data-stu-id="3c615-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="3c615-108">Na przykład jeśli metoda w zestawie A jest chroniony przez żądanie łącza, bezpośrednie obiekt wywołujący w zestawie B jest oceniany na podstawie uprawnień zestawu B.  Jednak zapotrzebowanie na łącza nie oceni metody w zestawie C, jeśli pośrednio wywołuje metodę w zestawie A przy użyciu metody w zestawie B. Żądanie łącza określa tylko uprawnienia bezpośrednich wywołań w zestawie wywołania natychmiastowego musi mieć link do kodu.</span><span class="sxs-lookup"><span data-stu-id="3c615-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="3c615-109">Nie określa uprawnień, które muszą mieć wszystkie osoby wywołujące do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="3c615-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="3c615-110">Modyfikatory <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>i <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk nie wpływają na ocenę żądań łączy.</span><span class="sxs-lookup"><span data-stu-id="3c615-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="3c615-111">Ponieważ żądania łącza nie wykonują spacer stosu, modyfikatory spacer stosu nie mają wpływu na żądania łącza.</span><span class="sxs-lookup"><span data-stu-id="3c615-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="3c615-112">Jeśli metoda chroniona przez żądanie łącza jest dostępna za pośrednictwem [odbicia,](../reflection-and-codedom/reflection.md)żądanie łącza sprawdza bezpośrednie wywołanie kodu dostępnego za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="3c615-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="3c615-113">Dotyczy to zarówno odnajdowania metody, jak i wywołania metody wykonywanego przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="3c615-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="3c615-114">Załóżmy na przykład, że <xref:System.Reflection.MethodInfo> kod używa odbicia do zwrócenia obiektu reprezentującego metodę chroniona przez żądanie łącza, a następnie przekazuje ten **obiekt MethodInfo** do innego kodu, który używa obiektu do wywołania oryginalnej metody.</span><span class="sxs-lookup"><span data-stu-id="3c615-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="3c615-115">W takim przypadku sprawdzanie popytu łącza występuje dwa razy: raz dla kodu, który zwraca **MethodInfo** obiektu i raz dla kodu, który wywołuje go.</span><span class="sxs-lookup"><span data-stu-id="3c615-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c615-116">Żądanie łącza wykonywane na konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżką wykonywania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c615-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="3c615-117">W rezultacie, gdy żądanie łącza jest stosowane do całej klasy, nie można chronić dostęp do konstruktora statycznego, chociaż nie chroni resztę klasy.</span><span class="sxs-lookup"><span data-stu-id="3c615-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="3c615-118">Poniższy fragment kodu deklaratywnie określa, `ReadData` że każdy `CustomPermission` kod łączący się z metodą musi mieć uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="3c615-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="3c615-119">To uprawnienie jest hipotetyczne uprawnienie niestandardowe i nie istnieje w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c615-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="3c615-120">Żądanie jest dokonywane przez przekazanie **SecurityAction.LinkDemand** flagi do `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="3c615-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c615-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c615-121">See also</span></span>

- [<span data-ttu-id="3c615-122">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3c615-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="3c615-123">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="3c615-123">Code Access Security</span></span>](code-access-security.md)
