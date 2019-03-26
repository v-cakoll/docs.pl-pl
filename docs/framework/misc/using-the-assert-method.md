---
title: Korzystanie z metody Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5799ab8e827305fca565064a0ae7290c6c19eb01
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463010"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="fb601-102">Korzystanie z metody Assert</span><span class="sxs-lookup"><span data-stu-id="fb601-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="fb601-103"><xref:System.Security.CodeAccessPermission.Assert%2A> jest to metoda może być wywoływana w klasach uprawnienia dostępu kodu i na <xref:System.Security.PermissionSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="fb601-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="fb601-104">Możesz użyć **Asercja** aby umożliwić kod (i wywoływania podrzędnego) do wykonania akcji, które Twój kod ma uprawnienie do wykonywania, ale wywołujące może nie masz uprawnienia do wykonania.</span><span class="sxs-lookup"><span data-stu-id="fb601-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="fb601-105">Potwierdzenie zabezpieczeń zmienia normalnego procesu, jak środowisko uruchomieniowe wykonuje podczas sprawdzania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fb601-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="fb601-106">Uprawnienie jest assert, informuje o system zabezpieczeń nie, aby sprawdzić obiektów wywołujących swój kod pod kątem potwierdzone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fb601-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fb601-107">Używać asercji ostrożnie, ponieważ mogą otworzyć luk w zabezpieczeniach i podważać mechanizmu wymuszania ograniczeń zabezpieczeń w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="fb601-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="fb601-108">Potwierdzenia są przydatne w sytuacjach, w których bibliotekę wywołuje kod niezarządzany lub sprawia, że wywołanie, które wymaga uprawnień, które oczywiście nie jest powiązana z zamierzonym użyciem bibliotek.</span><span class="sxs-lookup"><span data-stu-id="fb601-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="fb601-109">Na przykład, wszystkie zarządzane kod, który wywołuje kod niezarządzany musi mieć **SecurityPermission** z **UnmanagedCode** określono flagę.</span><span class="sxs-lookup"><span data-stu-id="fb601-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="fb601-110">Kod, który nie pochodzi z komputera lokalnego, takie jak kod, który jest pobierany z lokalny intranet, nie otrzyma tego uprawnienia domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fb601-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="fb601-111">W związku z tym aby kod, który jest pobierany z lokalny intranet, aby można było wywołać bibliotekę, która korzysta z kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="fb601-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="fb601-112">Ponadto niektóre biblioteki może wykonywać wywołania, są niewidoczne dla kodu wywołującego, które wymagają specjalnych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fb601-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="fb601-113">Umożliwia także potwierdzenia w sytuacjach, w których kod uzyskuje dostęp do zasobów w sposób, który jest całkowicie ukryte z wywołującym.</span><span class="sxs-lookup"><span data-stu-id="fb601-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="fb601-114">Na przykład załóżmy, że Twoja biblioteka uzyskuje informacje z bazy danych, ale w procesie również odczytuje informacje z rejestru komputera.</span><span class="sxs-lookup"><span data-stu-id="fb601-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="fb601-115">Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mają żadnej możliwość określenia, czy ich kod wymaga **RegistryPermission** aby można było używać kodu.</span><span class="sxs-lookup"><span data-stu-id="fb601-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="fb601-116">W tym przypadku Jeśli zdecydujesz, że nie jest uzasadnione i konieczne wymagają wywoływania w kodzie miał uprawnienia do dostępu do rejestru, możesz assert uprawnień do odczytywania z rejestru.</span><span class="sxs-lookup"><span data-stu-id="fb601-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="fb601-117">W tej sytuacji jest odpowiednie dla biblioteki do potwierdzenia zgody, tak że obiekty wywołujące, bez **RegistryPermission** biblioteki można używać.</span><span class="sxs-lookup"><span data-stu-id="fb601-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="fb601-118">Potwierdzenie wpływa na przejście przez stos tylko wtedy, gdy jest to potwierdzone uprawnienia i uprawnienia wymagane przez obiekt wywołujący podrzędne są tego samego typu, a Jeśli żądane uprawnienie jest podzbiorem potwierdzone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fb601-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="fb601-119">Na przykład, jeśli użytkownik asercja **FileIOPermission** można odczytać wszystkich plików na dysku C, a żądanie podrzędne wykonywane **FileIOPermission** odczytywać pliki w C:\Temp, potwierdzenie mogą mieć wpływ na stosów; Jednakże jeśli żądanie dotyczyło **FileIOPermission** do zapisu na dysku C, potwierdzenie miałaby żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="fb601-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="fb601-120">Aby wykonać potwierdzenia, kod musi otrzymać uprawnienia są potwierdzające i <xref:System.Security.Permissions.SecurityPermission> reprezentujący prawo do wprowadzania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="fb601-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="fb601-121">Mimo że można assert uprawnienia, które nie udzielono kodu i potwierdzenie byłaby sensu, ponieważ kontrola zabezpieczeń może zakończyć się niepowodzeniem, zanim potwierdzenie może spowodować, że powiodło się.</span><span class="sxs-lookup"><span data-stu-id="fb601-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="fb601-122">Na poniższej ilustracji przedstawiono, co się stanie, gdy używasz **Asercja**.</span><span class="sxs-lookup"><span data-stu-id="fb601-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="fb601-123">Załóżmy, że następujące instrukcje są spełnione dotyczące zestawów A, B, C, E i f. i uprawnienia P1 i P1A:</span><span class="sxs-lookup"><span data-stu-id="fb601-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="fb601-124">P1A reprezentuje uprawnienie do odczytu plików txt na dysku C.</span><span class="sxs-lookup"><span data-stu-id="fb601-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="fb601-125">P1 reprezentuje uprawnienie do odczytu wszystkich plików na dysku C.</span><span class="sxs-lookup"><span data-stu-id="fb601-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="fb601-126">To P1 i P1A **FileIOPermission** typów i P1A jest podzbiorem P1.</span><span class="sxs-lookup"><span data-stu-id="fb601-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="fb601-127">Zestawy E i f. przyznano uprawnienie P1A.</span><span class="sxs-lookup"><span data-stu-id="fb601-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="fb601-128">Zestaw C ma uprawnienia P1.</span><span class="sxs-lookup"><span data-stu-id="fb601-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="fb601-129">Zestawy, A i B ma odpowiednie uprawnienia P1A ani P1.</span><span class="sxs-lookup"><span data-stu-id="fb601-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="fb601-130">Metoda A znajduje się w zestawie A, metoda B jest zawarty w zestawie B i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fb601-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram pokazujący zestawy metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="fb601-132">W tym scenariuszu, metoda A wywołuje usługę B, wywołania B, C, wywołania C E, wywołania E F. Metoda C potwierdza uprawnienie do odczytania plików na dysku C (uprawnienie P1) i metody E żądania uprawnień do odczytu plików txt na dysku C (uprawnienie P1A).</span><span class="sxs-lookup"><span data-stu-id="fb601-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="fb601-133">Po napotkaniu w czasie wykonywania żądanie w F przeszukiwania stosu jest wykonywane, aby sprawdzić uprawnienia wszystkich obiektów wywołujących f, począwszy od E. E ma uprawnienia P1A, więc przeszukiwania stosu przechodzi do sprawdzania uprawnień C, gdzie odnaleziono potwierdzenia C.</span><span class="sxs-lookup"><span data-stu-id="fb601-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="fb601-134">Ponieważ żądane uprawnienia (P1A) jest podzbiorem potwierdzone uprawnienia (P1), zatrzymanie przeszukiwania stosu i sprawdzanie zabezpieczeń automatycznie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fb601-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="fb601-135">Nie ma znaczenia w tym zestawów, które A i B nie przyznano uprawnień P1A.</span><span class="sxs-lookup"><span data-stu-id="fb601-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="fb601-136">Potwierdzanie P1, Metoda C zapewnia wywołujące dostęp zasobów chronionych przez P1, nawet wtedy, gdy funkcja wywołująca nie przyznano uprawnień dostępu do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="fb601-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="fb601-137">Jeśli projekt biblioteki klas, klasa uzyskuje dostęp do chronionego zasobu w większości przypadków należy żądania zabezpieczeń wymaga, że funkcja wywołująca klasy mają odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fb601-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="fb601-138">Jeśli klasy następnie wykonuje operację na, którym wiadomo, większość wywołujące nie będziesz mieć uprawnienia, a jeśli pragnących odpowiedzialność umożliwiając te obiekty wywołujące wywołać kod można assert uprawnienia, wywołując **Asercja** metody na obiekt uprawnień, który reprezentuje operację wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="fb601-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="fb601-139">Za pomocą **Asercja** w ten sposób umożliwia wywołań, w których zwykle nie może wykonać to wywołanie kodu.</span><span class="sxs-lookup"><span data-stu-id="fb601-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="fb601-140">W związku z tym jeśli uprawnienie jest assert, należy koniecznie kontrole zabezpieczeń odpowiednich wcześniej aby zapobiec niewłaściwemu składnika.</span><span class="sxs-lookup"><span data-stu-id="fb601-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="fb601-141">Na przykład załóżmy, że klasa wysoce zaufanym biblioteka ma metodę, która usuwa pliki.</span><span class="sxs-lookup"><span data-stu-id="fb601-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="fb601-142">Plik uzyskuje dostęp przez wywołanie funkcji Win32 niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fb601-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="fb601-143">Obiekt wywołujący wywołuje kodu **Usuń** metodę przekazywania pliku, który zostanie usunięty, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="fb601-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="fb601-144">W ramach **Usuń** tworzy kodzie metody <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący C:\Test.txt dostęp do zapisu.</span><span class="sxs-lookup"><span data-stu-id="fb601-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="fb601-145">(Dostęp do zapisu jest wymagane do usunięcia pliku). Następnie kod wywołuje imperatywne sprawdzanie zabezpieczeń, wywołując **FileIOPermission** obiektu **żądanie** metody.</span><span class="sxs-lookup"><span data-stu-id="fb601-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="fb601-146">Jeśli jeden z obiektów wywołujących w stosie wywołań nie ma to uprawnienie <xref:System.Security.SecurityException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="fb601-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="fb601-147">Jeśli jest zgłaszany żaden wyjątek, wiesz, że wszystkie obiekty wywołujące mają prawa dostępu C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="fb601-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="fb601-148">Ponieważ uważasz, że większość wywołań usługi nie ma uprawnienia do dostępu do kodu niezarządzanego, kodzie następnie tworzy <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje po prawej stronie, aby wywoływać kod niezarządzany, a następnie wywołuje obiekt **Asercja** metody.</span><span class="sxs-lookup"><span data-stu-id="fb601-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="fb601-149">Na koniec wywołuje funkcję Win32 niezarządzanych w celu usunięcia C:\Text.txt i przekazuje sterowanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fb601-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fb601-150">Należy upewnić się, że Twój kod nie potwierdzenia w sytuacjach, w którym kod może służyć przez inny kod dostępu do zasobu, który jest chroniony przez uprawnienia, które są potwierdzające.</span><span class="sxs-lookup"><span data-stu-id="fb601-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="fb601-151">Na przykład w kodzie, który zapisuje dane w pliku, którego nazwa jest określona przez obiekt wywołujący, jako parametr, użytkownik będzie nie asercja **FileIOPermission** do zapisu do plików, ponieważ kod jest otwarte nieuprawnione użycie przez inną firmę.</span><span class="sxs-lookup"><span data-stu-id="fb601-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="fb601-152">Gdy używasz składnia zabezpieczeń imperatywnych, wywołanie **Asercja** metody na wiele uprawnień w tej samej metody powoduje, że zostanie wygenerowany wyjątek zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fb601-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="fb601-153">Zamiast tego należy utworzyć **PermissionSet** obiektów, przekazać go indywidualne uprawnienia, które chcesz wywołać, a następnie wywołaj **Asercja** metody **PermissionSet** obiekt.</span><span class="sxs-lookup"><span data-stu-id="fb601-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="fb601-154">Możesz wywołać **Asercja** metoda więcej niż jeden raz na zastosowania składnia zabezpieczeń deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="fb601-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="fb601-155">W poniższym przykładzie pokazano składni deklaratywnej dla bezpieczeństwa, który umożliwia sprawdzenie za pomocą **Asercja** metody.</span><span class="sxs-lookup"><span data-stu-id="fb601-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="fb601-156">Należy zauważyć, że **FileIOPermissionAttribute** składni przyjmuje dwie wartości: <xref:System.Security.Permissions.SecurityAction> wyliczenie i lokalizację pliku lub katalogu, do którego ma zostać udzielone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fb601-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="fb601-157">Wywołanie **Asercja** powoduje, że żądania w celu uzyskania dostępu do `C:\Log.txt` została wykonana pomyślnie, nawet jeśli obiekty wywołujące nie są sprawdzane pod kątem uprawnienia dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="fb601-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 <span data-ttu-id="fb601-158">Poniższe fragmenty kodu pokazują składnia imperatywna, dla bezpieczeństwa, który umożliwia sprawdzenie za pomocą **Asercja** metody.</span><span class="sxs-lookup"><span data-stu-id="fb601-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="fb601-159">W tym przykładzie wystąpienie **FileIOPermission** obiekt nie został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="fb601-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="fb601-160">Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** zdefiniować typ dostępu przyznany, następuje ciąg opisujący lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="fb601-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="fb601-161">Raz **FileIOPermission** obiekt jest zdefiniowany, musisz wywołać jej **Asercja** metody do przesłonięcia sprawdzanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fb601-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb601-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb601-162">See also</span></span>
- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="fb601-163">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb601-163">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="fb601-164">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="fb601-164">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
