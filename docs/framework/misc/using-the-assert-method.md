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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181102"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="9c64f-102">Korzystanie z metody Assert</span><span class="sxs-lookup"><span data-stu-id="9c64f-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="9c64f-103"><xref:System.Security.CodeAccessPermission.Assert%2A>jest metodą, która może być wywoływana <xref:System.Security.PermissionSet> na klasy uprawnień dostępu do kodu i klasy.</span><span class="sxs-lookup"><span data-stu-id="9c64f-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="9c64f-104">Można użyć **Assert,** aby włączyć kod (i podrzędnych wywołań) do wykonywania akcji, które kod ma uprawnienia do zrobienia, ale jego wywołujących może nie mieć uprawnień do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="9c64f-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="9c64f-105">Asercja zabezpieczeń zmienia normalny proces, który środowisko wykonawcze wykonuje podczas sprawdzania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9c64f-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="9c64f-106">Gdy dochodzisz uprawnienia, informuje system zabezpieczeń, aby nie sprawdzać wywołań kodu dla potwierdzonych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="9c64f-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9c64f-107">Używaj potwierdzeń ostrożnie, ponieważ mogą one otworzyć luki w zabezpieczeniach i podważyć mechanizm wykonywania ograniczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9c64f-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="9c64f-108">Potwierdzenia są przydatne w sytuacjach, w których biblioteka wywołuje do kodu niezarządzanego lub wywołuje, który wymaga uprawnienia, które nie jest oczywiście związane z zamierzonego użycia biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9c64f-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="9c64f-109">Na przykład cały kod zarządzany, który wywołuje do kodu niezarządzanego musi mieć **SecurityPermission** z **UnmanagedCode** flagi określone.</span><span class="sxs-lookup"><span data-stu-id="9c64f-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="9c64f-110">Kod, który nie pochodzi z komputera lokalnego, na przykład kod pobrany z lokalnego intranetu, nie zostanie domyślnie przyznany temu uprawnieniu.</span><span class="sxs-lookup"><span data-stu-id="9c64f-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="9c64f-111">W związku z tym w celu kodu, który jest pobierany z lokalnego intranetu, aby móc wywołać bibliotekę, która używa kodu niezarządzanego, musi mieć uprawnienia potwierdzone przez bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="9c64f-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="9c64f-112">Ponadto niektóre biblioteki mogą wykonywać wywołania, które są niewidoczne dla osób wywołujących i wymagają specjalnych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="9c64f-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="9c64f-113">Można również użyć potwierdzeń w sytuacjach, w których kod uzyskuje dostęp do zasobu w sposób, który jest całkowicie ukryty przed obiektami wywołującymi.</span><span class="sxs-lookup"><span data-stu-id="9c64f-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="9c64f-114">Załóżmy na przykład, że biblioteka uzyskuje informacje z bazy danych, ale w procesie odczytuje również informacje z rejestru komputera.</span><span class="sxs-lookup"><span data-stu-id="9c64f-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="9c64f-115">Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mają możliwości poznania, że ich kod wymaga **RegistryPermission** w celu użycia kodu.</span><span class="sxs-lookup"><span data-stu-id="9c64f-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="9c64f-116">W takim przypadku, jeśli zdecydujesz, że nie jest uzasadnione lub konieczne, aby wymagać, aby osoby wywołujące kodu mają uprawnienia dostępu do rejestru, można dochodzić uprawnień do odczytu rejestru.</span><span class="sxs-lookup"><span data-stu-id="9c64f-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="9c64f-117">W tej sytuacji jest właściwe dla biblioteki do potwierdzenia uprawnienia, tak aby wywołania bez **RegistryPermission** można użyć biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9c64f-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="9c64f-118">Twierdzenie wpływa na spacer stosu tylko wtedy, gdy potwierdzone uprawnienie i uprawnienie wymagane przez wywołującego podrzędnego są tego samego typu i jeśli wymagane uprawnienie jest podzbiorem potwierdzonego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9c64f-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="9c64f-119">Na przykład jeśli potwierdzić **FileIOPermission** do odczytu wszystkich plików na dysku C i podrzędne żądanie jest dla **FileIOPermission** do odczytu plików w C:\Temp, twierdzenie może mieć wpływ na spacer stosu; jednak jeśli żądanie było **fileiopermission** do zapisu na dysku C, twierdzenie nie miałoby wpływu.</span><span class="sxs-lookup"><span data-stu-id="9c64f-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="9c64f-120">Aby wykonać potwierdzenia, kod musi być przyznane zarówno uprawnienia, <xref:System.Security.Permissions.SecurityPermission> które są twierdząc i który reprezentuje prawo do potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="9c64f-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="9c64f-121">Chociaż można potwierdzić uprawnienia, które kod nie został przyznany, twierdzenie byłoby bezcelowe, ponieważ sprawdzanie zabezpieczeń zakończy się niepowodzeniem, zanim twierdzenie może spowodować jego powodowie.</span><span class="sxs-lookup"><span data-stu-id="9c64f-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="9c64f-122">Na poniższej ilustracji przedstawiono, co się dzieje, gdy używasz **Assert**.</span><span class="sxs-lookup"><span data-stu-id="9c64f-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="9c64f-123">Załóżmy, że następujące instrukcje są prawdziwe dotyczące zestawów A, B, C, E i F i dwa uprawnienia, P1 i P1A:</span><span class="sxs-lookup"><span data-stu-id="9c64f-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="9c64f-124">P1A reprezentuje prawo do odczytu plików .txt na dysku C.</span><span class="sxs-lookup"><span data-stu-id="9c64f-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="9c64f-125">P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.</span><span class="sxs-lookup"><span data-stu-id="9c64f-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="9c64f-126">P1A i P1 są typami **FileIOPermission,** a P1A jest podzbiorem P1.</span><span class="sxs-lookup"><span data-stu-id="9c64f-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="9c64f-127">Zestawy E i F otrzymały uprawnienie P1A.</span><span class="sxs-lookup"><span data-stu-id="9c64f-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="9c64f-128">Zestaw C otrzymał uprawnienie P1.</span><span class="sxs-lookup"><span data-stu-id="9c64f-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="9c64f-129">Zestawy A i B nie zostały przyznane ani P1, ani P1A uprawnień.</span><span class="sxs-lookup"><span data-stu-id="9c64f-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="9c64f-130">Metoda A jest zawarta w zestawie A, metoda B jest zawarta w zestawie B i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9c64f-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram, który pokazuje Assert zestawy metody.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="9c64f-132">W tym scenariuszu metoda A wywołuje B, B wywołuje C, C wywołuje E i E wywołuje F. Metoda C potwierdza uprawnienia do odczytu plików na dysku C (uprawnienie P1), a metoda E wymaga uprawnień do odczytu plików .txt na dysku C (uprawnienie P1A).</span><span class="sxs-lookup"><span data-stu-id="9c64f-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="9c64f-133">Gdy żądanie w F zostanie napotkane w czasie wykonywania, spacer stosu jest wykonywane, aby sprawdzić uprawnienia wszystkich wywołujących F, począwszy od E. E otrzymał uprawnienia P1A, więc stos przejść przechodzi do zbadania uprawnień C, gdzie twierdzenie C jest odnaleziony.</span><span class="sxs-lookup"><span data-stu-id="9c64f-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="9c64f-134">Ponieważ żądane uprawnienie (P1A) jest podzbiorem potwierdzonego uprawnienia (P1), przejście stosu zatrzymuje się, a sprawdzanie zabezpieczeń zostanie automatycznie pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9c64f-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="9c64f-135">Nie ma znaczenia, że zestawy A i B nie otrzymały uprawnień P1A.</span><span class="sxs-lookup"><span data-stu-id="9c64f-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="9c64f-136">Potwierdzając P1, metoda C zapewnia, że jego wywołujących można uzyskać dostęp do zasobu chronionego przez P1, nawet jeśli wywołujących nie zostały przyznane uprawnienia dostępu do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="9c64f-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="9c64f-137">Jeśli projektujesz bibliotekę klas i klasa uzyskuje dostęp do chronionego zasobu, w większości przypadków należy wysilić żądanie zabezpieczeń wymagające, aby osoby wywołujące klasy miały odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9c64f-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="9c64f-138">Jeśli klasa następnie wykonuje operację, dla której wiadomo, że większość jego wywołujących nie będzie miał uprawnień, a jeśli chcesz wziąć odpowiedzialność za umożliwienie tych wywołujących wywołać kod, można potwierdzić uprawnienia wywołując **Assert** metody na obiekt uprawnień, który reprezentuje operację, którą wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="9c64f-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="9c64f-139">Za pomocą **Assert** w ten sposób umożliwia wywołujących, które normalnie nie można tego zrobić, więc wywołać kod.</span><span class="sxs-lookup"><span data-stu-id="9c64f-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="9c64f-140">W związku z tym jeśli potwierdzisz uprawnienie, należy upewnić się, że należy wykonać odpowiednie kontrole zabezpieczeń wcześniej, aby zapobiec niewłaściwie składnika.</span><span class="sxs-lookup"><span data-stu-id="9c64f-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="9c64f-141">Załóżmy na przykład, że klasa biblioteki jest wysoce zaufana, która usuwa pliki.</span><span class="sxs-lookup"><span data-stu-id="9c64f-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="9c64f-142">Uzyskuje dostęp do pliku, wywołując niezarządzaną funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="9c64f-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="9c64f-143">Wywołujący wywołuje metodę **delete** kodu, przekazując w nazwie pliku do usunięcia, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="9c64f-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="9c64f-144">W ramach **Metody Delete** kod <xref:System.Security.Permissions.FileIOPermission> tworzy obiekt reprezentujący dostęp do zapisu do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="9c64f-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="9c64f-145">(Aby usunąć plik, wymagany jest dostęp do zapisu). Kod następnie wywołuje imperatywnych kontroli zabezpieczeń, wywołując **FileIOPermission** obiektu **Demand** metody.</span><span class="sxs-lookup"><span data-stu-id="9c64f-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="9c64f-146">Jeśli jeden z wywołujących w stosie wywołań <xref:System.Security.SecurityException> nie ma tego uprawnienia, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="9c64f-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="9c64f-147">Jeśli nie zostanie zgłoszony wyjątek, wiesz, że wszystkie obiekty wywołujące mają prawo dostępu do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="9c64f-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="9c64f-148">Ponieważ uważasz, że większość obiektów wywołujących nie będzie miał uprawnień dostępu <xref:System.Security.Permissions.SecurityPermission> do kodu niezarządzanego, kod następnie tworzy obiekt, który reprezentuje prawo do wywołania kodu niezarządzanego i wywołuje właściwego **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="9c64f-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="9c64f-149">Na koniec wywołuje niezarządzaną funkcję Win32, aby usunąć C:\Text.txt i zwraca kontrolę do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9c64f-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9c64f-150">Należy upewnić się, że kod nie używa potwierdzeń w sytuacjach, gdy kod może być używany przez inny kod, aby uzyskać dostęp do zasobu, który jest chroniony przez uprawnienie, które potwierdzasz.</span><span class="sxs-lookup"><span data-stu-id="9c64f-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="9c64f-151">Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez wywołującego jako parametr, nie można potwierdzić **FileIOPermission** do zapisywania do plików, ponieważ kod będzie otwarty do niewłaściwego użycia przez osobę trzecią.</span><span class="sxs-lookup"><span data-stu-id="9c64f-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="9c64f-152">Podczas korzystania ze składni zabezpieczeń imperatywów wywołanie **Assert** metody na wiele uprawnień w tej samej metodzie powoduje wyjątek zabezpieczeń do zaliczenia.</span><span class="sxs-lookup"><span data-stu-id="9c64f-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="9c64f-153">Zamiast tego należy utworzyć **Obiekt PermissionSet,** przekazać go poszczególnych uprawnień, które chcesz wywołać, a następnie **wywołać Assert** metody na **PermissionSet** obiektu.</span><span class="sxs-lookup"><span data-stu-id="9c64f-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="9c64f-154">Assert można **wywołać Assert** metody więcej niż jeden raz, gdy używasz składni zabezpieczeń deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="9c64f-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="9c64f-155">Poniższy przykład przedstawia składnię deklaratywną do zastępowania kontroli zabezpieczeń przy użyciu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="9c64f-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="9c64f-156">Należy zauważyć, że **FileIOPermissionAttribute** składni <xref:System.Security.Permissions.SecurityAction> ma dwie wartości: wyliczenie i lokalizacji pliku lub katalogu, do którego ma być przyznane uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="9c64f-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="9c64f-157">Wywołanie **Assert** powoduje żądania dostępu `C:\Log.txt` do pomyślnego, mimo że wywołujący nie są sprawdzane pod kątem uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="9c64f-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="9c64f-158">Następujące fragmenty kodu pokazują niezbędną składnię zastępowania kontroli zabezpieczeń przy użyciu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="9c64f-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="9c64f-159">W tym przykładzie jest deklarowane wystąpienie obiektu **FileIOPermission.**</span><span class="sxs-lookup"><span data-stu-id="9c64f-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="9c64f-160">Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** do definiowania typu dozwolonego dostępu, a następnie ciąg opisujący lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="9c64f-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="9c64f-161">Po zdefiniowaniu **FileIOPermission** obiekt, wystarczy wywołać jego **Assert** metody, aby zastąpić sprawdzanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9c64f-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c64f-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c64f-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="9c64f-163">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c64f-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="9c64f-164">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="9c64f-164">Code Access Security</span></span>](code-access-security.md)
