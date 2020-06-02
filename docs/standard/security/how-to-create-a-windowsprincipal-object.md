---
title: 'Porady: tworzenie obiektu WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 6064c98c4e1e5153f4e0de4849de196228972a89
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284432"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="888ad-102">Porady: tworzenie obiektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="888ad-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="888ad-103">Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiektu, w zależności od tego, czy kod musi wielokrotnie wykonywać walidację opartą na rolach, czy też musi wykonać tę operację tylko raz.</span><span class="sxs-lookup"><span data-stu-id="888ad-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="888ad-104">Jeśli kod musi wielokrotnie wykonywać walidację opartą na rolach, pierwsze z poniższych procedur generuje mniej kosztów.</span><span class="sxs-lookup"><span data-stu-id="888ad-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="888ad-105">Gdy kod musi wprowadzać walidacje oparte na rolach tylko raz, można utworzyć <xref:System.Security.Principal.WindowsPrincipal> Obiekt przy użyciu drugiego z poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="888ad-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="888ad-106">Aby utworzyć obiekt WindowsPrincipal do powtarzanej walidacji</span><span class="sxs-lookup"><span data-stu-id="888ad-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="888ad-107">Wywołaj <xref:System.AppDomain.SetPrincipalPolicy%2A> metodę dla <xref:System.AppDomain> obiektu, który jest zwracany przez właściwość statyczną <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> , przekazując metodę <xref:System.Security.Principal.PrincipalPolicy> wartości wyliczenia, która wskazuje, jakie nowe zasady powinny być.</span><span class="sxs-lookup"><span data-stu-id="888ad-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="888ad-108">Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> , i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> .</span><span class="sxs-lookup"><span data-stu-id="888ad-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="888ad-109">Poniższy kod ilustruje to wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="888ad-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="888ad-110">Za pomocą zestawu zasad należy użyć właściwości statycznej <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> do pobrania podmiotu zabezpieczeń, który hermetyzuje bieżącego użytkownika systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="888ad-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="888ad-111">Ponieważ typem zwracanym właściwości jest <xref:System.Security.Principal.IPrincipal> , należy rzutować wynik na <xref:System.Security.Principal.WindowsPrincipal> Typ.</span><span class="sxs-lookup"><span data-stu-id="888ad-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="888ad-112">Poniższy kod inicjuje nowy <xref:System.Security.Principal.WindowsPrincipal> obiekt do wartości podmiotu zabezpieczeń skojarzonego z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="888ad-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="888ad-113">Po utworzeniu obiektu podmiotu zabezpieczeń można użyć jednej z kilku metod weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="888ad-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="888ad-114">Aby utworzyć obiekt WindowsPrincipal na potrzeby pojedynczej walidacji</span><span class="sxs-lookup"><span data-stu-id="888ad-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="888ad-115">Zainicjuj nowy <xref:System.Security.Principal.WindowsIdentity> obiekt przez wywołanie metody statycznej <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> , która wysyła zapytanie do bieżącego konta systemu Windows i umieszcza informacje o tym koncie w nowo utworzonym obiekcie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="888ad-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="888ad-116">Poniższy kod tworzy nowy <xref:System.Security.Principal.WindowsIdentity> obiekt i inicjuje go dla bieżącego uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="888ad-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="888ad-117">Utwórz nowy <xref:System.Security.Principal.WindowsPrincipal> obiekt i przekaż go do wartości <xref:System.Security.Principal.WindowsIdentity> obiektu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="888ad-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="888ad-118">Po utworzeniu obiektu podmiotu zabezpieczeń można użyć jednej z kilku metod weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="888ad-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888ad-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="888ad-119">See also</span></span>

- [<span data-ttu-id="888ad-120">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="888ad-120">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
