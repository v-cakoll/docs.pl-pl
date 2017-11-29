---
title: Korzystanie z metody Assert
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a1627af9dd968a8a183a251d5352c62457f71e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-assert-method"></a><span data-ttu-id="fd537-102">Korzystanie z metody Assert</span><span class="sxs-lookup"><span data-stu-id="fd537-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="fd537-103"><xref:System.Security.CodeAccessPermission.Assert%2A>jest to metoda może być wywoływana dla klasy uprawnień dostępu kodu i na <xref:System.Security.PermissionSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="fd537-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="fd537-104">Można użyć **Assert** Aby włączyć kod (i wywoływania podrzędnego) do wykonywania akcji, które kod ma uprawnienie do wykonywania, ale jego wywołań może nie mieć odpowiednich uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fd537-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="fd537-105">Potwierdzenia zabezpieczeń zmienia normalny proces, który wykonuje środowiska uruchomieniowego podczas sprawdzania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fd537-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="fd537-106">Jeśli Potwierdzaj uprawnienia, informuje system zabezpieczeń nie, aby sprawdzić wywołań kodu potwierdzone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fd537-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fd537-107">Ostrożnie korzystaj potwierdzeń, ponieważ mogą otworzyć luk w zabezpieczeniach i obniżyć środowiska uruchomieniowego mechanizmu wymuszania ograniczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fd537-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="fd537-108">Potwierdzenia są przydatne w sytuacjach, w których biblioteki wywołania do kodu niezarządzanego lub nawiązuje połączenie, które wymaga uprawnień, które oczywiście nie jest powiązana z zamierzonym użyciem biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fd537-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="fd537-109">Na przykład wszystkie zarządzane kod, który musi mieć wywołania do kodu niezarządzanego **SecurityPermission** z **UnmanagedCode** określona flaga.</span><span class="sxs-lookup"><span data-stu-id="fd537-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="fd537-110">Kod, który nie pochodzi z komputera lokalnego, takie jak kod, który jest pobierana z lokalny intranet, zostanie nie można przyznać uprawnienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="fd537-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="fd537-111">W związku z tym aby kod, który jest pobierana z lokalny intranet, aby można było wywołać biblioteki, która korzysta z kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="fd537-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="fd537-112">Ponadto niektóre biblioteki może uniemożliwić wywołania są niewidoczne dla kodu wywołującego, które wymagają szczególnych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fd537-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="fd537-113">Umożliwia także potwierdzenia w sytuacjach, w których kod uzyskuje dostęp do zasobów w taki sposób, który jest całkowicie ukryty z wywołań.</span><span class="sxs-lookup"><span data-stu-id="fd537-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="fd537-114">Na przykład załóżmy, że biblioteka uzyskuje informacje z bazy danych, ale w procesie również odczytuje informacje z rejestru komputera.</span><span class="sxs-lookup"><span data-stu-id="fd537-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="fd537-115">Ponieważ deweloperów korzystających z biblioteki nie ma dostępu do źródła, ich nie ma możliwości wiedząc, że ich kod wymaga **RegistryPermission** aby można było używać kodu.</span><span class="sxs-lookup"><span data-stu-id="fd537-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="fd537-116">Jeśli zdecydujesz, że nie jest uzasadnione lub trzeba mieć wywołań kodu uprawnień dostępu do rejestru, można w takim przypadku assert uprawnień do odczytywania rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd537-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="fd537-117">W takiej sytuacji jest odpowiednie dla biblioteki do potwierdzenia uprawnienia, tak że wywołań bez **RegistryPermission** biblioteki można używać.</span><span class="sxs-lookup"><span data-stu-id="fd537-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="fd537-118">Potwierdzenie dotyczy przeszukiwania stosu tylko wtedy, gdy potwierdzone uprawnienia i wymagane przez obiekt wywołujący podrzędne są tego samego typu i Jeśli żądane uprawnienie jest podzbiorem potwierdzone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fd537-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="fd537-119">Na przykład, jeśli użytkownik assert **FileIOPermission** do odczytu wszystkich plików na dysku C, a żądanie podrzędne wykonywane **FileIOPermission** odczytywać pliki w C:\Temp, potwierdzenie mogą wpłynąć na przeszukiwania stosu; Jednak jeśli żądanie dotyczyło **FileIOPermission** zapisu na dysku C, potwierdzenie czy nie obowiązują.</span><span class="sxs-lookup"><span data-stu-id="fd537-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="fd537-120">Aby wykonać potwierdzeń, kodu musi otrzymać uprawnienia są zostanie i <xref:System.Security.Permissions.SecurityPermission> reprezentujący prawo do wprowadzania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="fd537-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="fd537-121">Mimo że można assert uprawnienia, które nie zostało udzielone kodu, potwierdzenie byłoby bezcelowe, ponieważ kontrola zabezpieczeń nie powiedzie się przed potwierdzenia może spowodować, że plik powiodło się.</span><span class="sxs-lookup"><span data-stu-id="fd537-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="fd537-122">Na poniższej ilustracji pokazano, co się dzieje, gdy używasz **Assert**.</span><span class="sxs-lookup"><span data-stu-id="fd537-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="fd537-123">Załóżmy, że następujące instrukcje są spełnione dotyczące zestawów A, B, C, E i F i uprawnienia P1 i P1A:</span><span class="sxs-lookup"><span data-stu-id="fd537-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="fd537-124">P1A reprezentuje prawo do odczytu dla plików txt na dysku C.</span><span class="sxs-lookup"><span data-stu-id="fd537-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="fd537-125">P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.</span><span class="sxs-lookup"><span data-stu-id="fd537-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="fd537-126">P1A i P1 są **FileIOPermission** typy i P1A jest podzbiorem P1.</span><span class="sxs-lookup"><span data-stu-id="fd537-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="fd537-127">Zestawy E i F przyznano uprawnienia P1A.</span><span class="sxs-lookup"><span data-stu-id="fd537-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="fd537-128">Zestaw C ma uprawnienia P1.</span><span class="sxs-lookup"><span data-stu-id="fd537-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="fd537-129">Zestawy, A i B ma odpowiednie uprawnienia P1 ani P1A.</span><span class="sxs-lookup"><span data-stu-id="fd537-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="fd537-130">Metoda jest zawarty w zestawie A, metoda B jest zawarty w zestawie B i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fd537-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 <span data-ttu-id="fd537-131">![](../../../docs/framework/misc/media/assert.gif "Assert")</span><span class="sxs-lookup"><span data-stu-id="fd537-131">![](../../../docs/framework/misc/media/assert.gif "assert")</span></span>  
<span data-ttu-id="fd537-132">Przy użyciu Assert</span><span class="sxs-lookup"><span data-stu-id="fd537-132">Using Assert</span></span>  
  
 <span data-ttu-id="fd537-133">W tym scenariuszu, wywołania metody A B, wywołania B C, wywołania C E i E wywołania F. Metoda C potwierdza uprawnień do odczytu plików na dysku C (uprawnienia P1), a metoda E żądania uprawnień do odczytu plików txt na dysku C (uprawnienie P1A).</span><span class="sxs-lookup"><span data-stu-id="fd537-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="fd537-134">Po napotkaniu popyt F w czasie wykonywania przeszukiwania stosu jest wykonywane, aby sprawdzić uprawnienia wszystkim zainteresowanym F, począwszy od E. E ma uprawnienia P1A, więc przeszukiwania stosu będzie kontynuowana, aby sprawdzić uprawnienia C, gdy zostanie wykryta potwierdzenia C.</span><span class="sxs-lookup"><span data-stu-id="fd537-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="fd537-135">Ponieważ żądane uprawnienie (P1A) jest podzbiorem potwierdzone uprawnienia (P1), zatrzymuje przeszukiwania stosu i sprawdzania zabezpieczeń automatycznie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fd537-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="fd537-136">Nie ma znaczenia, że zestawy, które A i B nie udzielono uprawnienia P1A.</span><span class="sxs-lookup"><span data-stu-id="fd537-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="fd537-137">Przez potwierdzające P1, Metoda C zapewnia, że elementy wywołujące pod można dostęp do zasobów chronionych przez P1, nawet jeśli wywołań nie przyznano uprawnień dostępu do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="fd537-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="fd537-138">Jeśli projektu biblioteki klas, klas uzyskuje dostęp do chronionych zasobów w większości przypadków należy żądania zabezpieczeń wymagających, że obiekty wywołujące klasy mają odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fd537-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="fd537-139">Jeśli klasa wykonuje następnie wykonanie operacji, które znasz większość elementy wywołujące pod nie będzie mieć uprawnień, a jeśli pragnących odpowiedzialność za umożliwienie tych wywołań wywołań kodu, można assert uprawnienia, wywołując **Assert** metody dla obiektu uprawnień, reprezentujący operację wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="fd537-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="fd537-140">Przy użyciu **Assert** w ten sposób umożliwia wywołań, które normalnie nie może wykonać tego wywołania kodu.</span><span class="sxs-lookup"><span data-stu-id="fd537-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="fd537-141">W związku z tym jeśli Potwierdzaj uprawnienia, należy koniecznie sprawdzania odpowiednich zabezpieczeń wcześniej aby zapobiec niewłaściwemu składnika.</span><span class="sxs-lookup"><span data-stu-id="fd537-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="fd537-142">Na przykład załóżmy, że klasa wysoce zaufanych biblioteka ma metodę, która usuwa pliki.</span><span class="sxs-lookup"><span data-stu-id="fd537-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="fd537-143">Uzyskuje dostęp do pliku przez wywołanie funkcji niezarządzanej Win32.</span><span class="sxs-lookup"><span data-stu-id="fd537-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="fd537-144">Obiekt wywołujący wywołuje swój kod **usunąć** metoda przekazywania pliku, który zostanie usunięty, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="fd537-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="fd537-145">W ramach **usunąć** tworzy kod metody <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący C:\Test.txt dostęp do zapisu.</span><span class="sxs-lookup"><span data-stu-id="fd537-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="fd537-146">(Dostęp do zapisu jest wymagany do usunięcia pliku). Następnie kod wywołuje wyboru zabezpieczenia imperatywne przez wywołanie metody **FileIOPermission** obiektu **żądanie** metody.</span><span class="sxs-lookup"><span data-stu-id="fd537-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="fd537-147">Jeśli jeden z obiektów wywołujących na stosie wywołań nie ma to uprawnienie <xref:System.Security.SecurityException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="fd537-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="fd537-148">Jeśli żaden wyjątek jest zgłaszany, wiadomo, że wszystkim zainteresowanym mają prawa dostępu C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="fd537-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="fd537-149">Ponieważ uważasz, że większość z wywołań nie będzie mieć uprawnień dostęp do kodu niezarządzanego, następnie tworzy kod <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje prawo do wywoływanie kodu niezarządzanego i wywołuje metodę obiektu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="fd537-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="fd537-150">Na koniec wywołania funkcji niezarządzanej Win32, aby usunąć C:\Text.txt i zwraca sterowania do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fd537-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fd537-151">Należy upewnić się, że kod nie używa potwierdzenia w sytuacjach, gdy Twoje kod może być używany przez inny kod dostępu do zasobu, która jest chroniona przez uprawnienia, które są zostanie.</span><span class="sxs-lookup"><span data-stu-id="fd537-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="fd537-152">Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez obiekt wywołujący jako parametru, użytkownik może nie assert **FileIOPermission** do zapisu do plików, ponieważ kod jest otwarte nieprawidłowego użycia przez inną firmę.</span><span class="sxs-lookup"><span data-stu-id="fd537-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="fd537-153">Gdy używasz składni zabezpieczenia imperatywne wywoływania **Assert** metody na wiele uprawnień w tej samej metody powoduje, że zostanie wygenerowany wyjątek zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fd537-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="fd537-154">Zamiast tego należy utworzyć **PermissionSet** obiektów, przekazywanie ich indywidualnych uprawnień, aby wywołać, a następnie wywołać **Assert** metoda **PermissionSet** obiekt.</span><span class="sxs-lookup"><span data-stu-id="fd537-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="fd537-155">Możesz wywołać **Assert** więcej niż jeden raz po użyj składni zabezpieczenia deklaratywne metody.</span><span class="sxs-lookup"><span data-stu-id="fd537-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="fd537-156">W poniższym przykładzie przedstawiono składni deklaratywnej kontroli bezpieczeństwa przy użyciu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="fd537-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="fd537-157">Zwróć uwagę, że **FileIOPermissionAttribute** składni ma dwie wartości: <xref:System.Security.Permissions.SecurityAction> wyliczenie i lokalizację pliku lub katalogu, do której ma zostać udzielone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="fd537-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="fd537-158">Wywołanie **Assert** powoduje, że żądania dostępu do `C:\Log.txt` zakończyła się powodzeniem, nawet jeśli wywołań nie są sprawdzane pod kątem uprawnienia dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="fd537-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="fd537-159">Poniższe fragmenty kodu Pokaż składni konieczne kontroli bezpieczeństwa przy użyciu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="fd537-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="fd537-160">W tym przykładzie wystąpienia **FileIOPermission** jest zadeklarowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="fd537-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="fd537-161">Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** do definiowania typu dostępu dozwolone, a następnie ciąg opisujący lokalizacji pliku.</span><span class="sxs-lookup"><span data-stu-id="fd537-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="fd537-162">Raz **FileIOPermission** obiektu jest zdefiniowana, należy wywołać jej **Assert** metody do przesłonięcia sprawdzanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fd537-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd537-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd537-163">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="fd537-164">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd537-164">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="fd537-165">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="fd537-165">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
