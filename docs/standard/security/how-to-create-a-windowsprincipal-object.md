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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77d86e2ade841b715fc4bea8350d4e043bcb91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="1087f-102">Porady: tworzenie obiektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="1087f-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="1087f-103">Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiektu, w zależności od tego, czy kod musi wielokrotnie sprawdzania poprawności opartego na rolach lub wykonaj jego tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1087f-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="1087f-104">Jeśli kod wielokrotnie wykonać weryfikacji opartej na rolach, pierwsza z poniższych procedur tworzy mniejsze koszty.</span><span class="sxs-lookup"><span data-stu-id="1087f-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="1087f-105">Gdy kod musi wprowadzić opartej na rolach sprawdzanie poprawności tylko raz, mogą tworzyć <xref:System.Security.Principal.WindowsPrincipal> obiektu za pomocą drugiego z poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="1087f-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="1087f-106">Aby utworzyć obiekt WindowsPrincipal do weryfikacji powtórzony</span><span class="sxs-lookup"><span data-stu-id="1087f-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1.  <span data-ttu-id="1087f-107">Wywołania <xref:System.AppDomain.SetPrincipalPolicy%2A> metoda <xref:System.AppDomain> obiektu, który jest zwracany przez statycznych <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwości przekazywanie metody <xref:System.Security.Principal.PrincipalPolicy> wartość wyliczenia wskazująca, jakie nowych zasad powinny być.</span><span class="sxs-lookup"><span data-stu-id="1087f-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="1087f-108">Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="1087f-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="1087f-109">Poniższy kod przedstawia wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="1087f-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  <span data-ttu-id="1087f-110">Z zasadami, należy ustawić, użyj statycznych <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwość, aby pobrać podmiot zabezpieczeń, który hermetyzuje bieżącego użytkownika systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1087f-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="1087f-111">Ponieważ właściwość zwracany typ jest <xref:System.Security.Principal.IPrincipal>, należy rzutować wynik, który ma <xref:System.Security.Principal.WindowsPrincipal> typu.</span><span class="sxs-lookup"><span data-stu-id="1087f-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="1087f-112">Poniższy kod inicjuje nowy <xref:System.Security.Principal.WindowsPrincipal> obiektu do wartości podmiot zabezpieczeń skojarzony z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="1087f-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  <span data-ttu-id="1087f-113">Gdy utworzono obiekt główny, umożliwia jedną z kilku metod go zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="1087f-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="1087f-114">Aby utworzyć obiekt WindowsPrincipal dla pojedynczego sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="1087f-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1.  <span data-ttu-id="1087f-115">Zainicjuj nowy <xref:System.Security.Principal.WindowsIdentity> obiektu przez wywołanie metody statycznych <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metodę, która wysyła zapytanie do konta systemu Windows i umieszcza informacje o tym koncie w tożsamości nowo utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="1087f-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="1087f-116">Poniższy kod tworzy nową <xref:System.Security.Principal.WindowsIdentity> obiektu i inicjuje ją do bieżącego użytkownika uwierzytelnionego.</span><span class="sxs-lookup"><span data-stu-id="1087f-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <span data-ttu-id="1087f-117">Utwórz nową <xref:System.Security.Principal.WindowsPrincipal> obiektu i przekaż go wartość <xref:System.Security.Principal.WindowsIdentity> obiekt utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="1087f-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  <span data-ttu-id="1087f-118">Gdy utworzono obiekt główny, umożliwia jedną z kilku metod go zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="1087f-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1087f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1087f-119">See Also</span></span>  
 [<span data-ttu-id="1087f-120">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="1087f-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
