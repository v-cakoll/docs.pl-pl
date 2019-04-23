---
title: 'Instrukcje: Tworzenie obiektu WindowsPrincipal'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f298a7b036857e783efa128ce45ee8634ce993d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314464"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="3ed16-102">Instrukcje: Tworzenie obiektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="3ed16-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="3ed16-103">Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiekt, w zależności od tego, czy kod musi wielokrotnie weryfikowania opartej na rolach lub należy to wykonać tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3ed16-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="3ed16-104">Jeśli kod musi wykonać wielokrotnie Walidacja oparta na rolach, pierwsza z poniższych procedur powoduje mniejsze obciążenie.</span><span class="sxs-lookup"><span data-stu-id="3ed16-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="3ed16-105">Gdy kod musi wprowadzić walidacji opartej na rolach tylko raz, można utworzyć <xref:System.Security.Principal.WindowsPrincipal> obiektu za pomocą drugiego z poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="3ed16-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="3ed16-106">Do tworzenie obiektu WindowsPrincipal do wielokrotnego sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="3ed16-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="3ed16-107">Wywołaj <xref:System.AppDomain.SetPrincipalPolicy%2A> metody <xref:System.AppDomain> obiekt, który jest zwracany przez statyczną <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwość, przekazując metody <xref:System.Security.Principal.PrincipalPolicy> wartości wyliczenia, która wskazuje, jakie nowe zasady powinny być.</span><span class="sxs-lookup"><span data-stu-id="3ed16-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="3ed16-108">Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="3ed16-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="3ed16-109">Poniższy kod demonstruje wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="3ed16-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="3ed16-110">Za pomocą zasad należy ustawić, używa się statycznej <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwość służąca do pobierania jednostki, która hermetyzuje bieżącego użytkownika Windows.</span><span class="sxs-lookup"><span data-stu-id="3ed16-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="3ed16-111">Ponieważ typ zwracany przez właściwość <xref:System.Security.Principal.IPrincipal>, należy rzutować wynik, który ma <xref:System.Security.Principal.WindowsPrincipal> typu.</span><span class="sxs-lookup"><span data-stu-id="3ed16-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="3ed16-112">Inicjuje nowe wystąpienie następującego kodu <xref:System.Security.Principal.WindowsPrincipal> obiektu do wartości podmiot zabezpieczeń skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="3ed16-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. <span data-ttu-id="3ed16-113">Po utworzeniu obiektu podmiotu zabezpieczeń, można użyć jednej z kilku metod Aby zweryfikować, czy.</span><span class="sxs-lookup"><span data-stu-id="3ed16-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="3ed16-114">Do tworzenie obiektu WindowsPrincipal dla pojedynczego sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="3ed16-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="3ed16-115">Zainicjuj nowe <xref:System.Security.Principal.WindowsIdentity> obiektu przez wywołanie statycznego <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metody, która odpytuje bieżącego konta Windows, a następnie umieszcza informacji na temat tego konta do obiektu tożsamości nowo utworzony.</span><span class="sxs-lookup"><span data-stu-id="3ed16-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="3ed16-116">Poniższy kod tworzy nową <xref:System.Security.Principal.WindowsIdentity> obiektu i inicjuje go do aktualnego użytkownika uwierzytelnionego.</span><span class="sxs-lookup"><span data-stu-id="3ed16-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="3ed16-117">Utwórz nową <xref:System.Security.Principal.WindowsPrincipal> obiektu i przekaż go wartość <xref:System.Security.Principal.WindowsIdentity> obiekt utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="3ed16-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="3ed16-118">Po utworzeniu obiektu podmiotu zabezpieczeń, można użyć jednej z kilku metod Aby zweryfikować, czy.</span><span class="sxs-lookup"><span data-stu-id="3ed16-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed16-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ed16-119">See also</span></span>

- [<span data-ttu-id="3ed16-120">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="3ed16-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
