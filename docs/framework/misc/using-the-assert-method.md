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
ms.openlocfilehash: f43ba2963ec447e5193da73452537b2539c51857
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206036"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="b61ab-102">Korzystanie z metody Assert</span><span class="sxs-lookup"><span data-stu-id="b61ab-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="b61ab-103"><xref:System.Security.CodeAccessPermission.Assert%2A>to metoda, która może być wywoływana dla klas uprawnień dostępu kodu i <xref:System.Security.PermissionSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="b61ab-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="b61ab-104">Za pomocą potwierdzeń można włączyć kod (i obiekty podrzędne wywołujące), aby wykonać akcje, do których Twój kod ma uprawnienia, ale jego obiekty wywołujące mogą nie mieć uprawnień do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b61ab-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="b61ab-105">Potwierdzenie zabezpieczeń zmienia normalny proces wykonywany przez środowisko uruchomieniowe podczas sprawdzania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="b61ab-106">Po podaniu uprawnienia Nakazuje systemowi zabezpieczeń, aby nie sprawdzać obiektów wywołujących kod dla potwierdzonego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b61ab-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b61ab-107">Należy uważnie używać potwierdzeń, ponieważ mogą one otwierać otwory zabezpieczające i podważać mechanizm środowiska uruchomieniowego w celu wymuszenia ograniczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="b61ab-108">Potwierdzenia są przydatne w sytuacjach, w których biblioteka wywołuje kod niezarządzany lub wykonuje wywołanie, które wymaga uprawnień, które nie są oczywiście powiązane z zamierzonym użyciem biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b61ab-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="b61ab-109">Na przykład, cały kod zarządzany, który wywołuje w kodzie niezarządzanym, musi mieć **SecurityPermission** z określoną flagą **UnmanagedCode** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="b61ab-110">Kod, który nie pochodzi z komputera lokalnego, na przykład kod pobrany z lokalnego intranetu, nie zostanie domyślnie udzielony.</span><span class="sxs-lookup"><span data-stu-id="b61ab-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="b61ab-111">W związku z tym, aby kod pobrany z lokalnego intranetu mógł wywołać bibliotekę, która używa kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="b61ab-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="b61ab-112">Ponadto niektóre biblioteki mogą wykonywać wywołania, które nie są widoczne dla obiektów wywołujących i wymagają specjalnych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="b61ab-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="b61ab-113">Można również użyć potwierdzeń w sytuacjach, w których kod uzyskuje dostęp do zasobu w sposób całkowicie ukryty przez wywołujących.</span><span class="sxs-lookup"><span data-stu-id="b61ab-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="b61ab-114">Załóżmy na przykład, że biblioteka uzyskuje informacje z bazy danych, ale w procesie odczytuje również informacje z rejestru komputera.</span><span class="sxs-lookup"><span data-stu-id="b61ab-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="b61ab-115">Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mogą oni znać, że ich kod wymaga **RegistryPermission** , aby móc korzystać z kodu.</span><span class="sxs-lookup"><span data-stu-id="b61ab-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="b61ab-116">W takim przypadku, jeśli zdecydujesz, że nie jest to uzasadnione ani konieczne, aby wymagać, aby wywołujący kod miał uprawnienia dostępu do rejestru, możesz postanowić się, że uprawnienia do odczytu rejestru.</span><span class="sxs-lookup"><span data-stu-id="b61ab-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="b61ab-117">W takiej sytuacji odpowiednie jest, aby Biblioteka pomogła uzyskać odpowiednie uprawnienia, aby obiekty wywołujące bez **RegistryPermission** mogły korzystać z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b61ab-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="b61ab-118">Potwierdzenie ma wpływ na stos przeszukiwania tylko wtedy, gdy potwierdzone uprawnienie i uprawnienia, które są żądane przez obiekt wywołujący podrzędny, są tego samego typu, a żądanie z uprawnieniami jest podzbiorem potwierdzonego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b61ab-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="b61ab-119">Na przykład Jeśli postanowisz **FileIOPermission** o odczytaniu wszystkich plików na dysku C i przeniesieniu żądania podrzędnego dla **FileIOPermission** do odczytu plików w katalogu C:\Temp, potwierdzenie może wpłynąć na przechodzenie stosu; Jeśli jednak żądanie dotyczyło **FileIOPermission** zapisu na dysku C, potwierdzenie nie będzie miało żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="b61ab-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="b61ab-120">Aby wykonać potwierdzenia, Twój kod musi mieć przyznane zarówno odpowiednie uprawnienia, jak i <xref:System.Security.Permissions.SecurityPermission> , które reprezentuje prawo do wykonywania potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="b61ab-121">Mimo że można potwierdzić, że nie przyznano kodu, potwierdzenie byłoby niemożliwe, ponieważ sprawdzenie zabezpieczeń zakończy się niepowodzeniem, aby potwierdzić pomyślne.</span><span class="sxs-lookup"><span data-stu-id="b61ab-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="b61ab-122">Na poniższej ilustracji pokazano, co się dzieje wprzypadku użycia potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="b61ab-123">Załóżmy, że następujące instrukcje są prawdziwe o zestawach A, B, C, E i F oraz dwóch uprawnieniach, P1 i P1A:</span><span class="sxs-lookup"><span data-stu-id="b61ab-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="b61ab-124">P1A reprezentuje prawo do odczytu plików txt na dysku C.</span><span class="sxs-lookup"><span data-stu-id="b61ab-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="b61ab-125">P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.</span><span class="sxs-lookup"><span data-stu-id="b61ab-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="b61ab-126">P1A i P1 są typami **FileIOPermission** , a P1A jest podzbiorem P1.</span><span class="sxs-lookup"><span data-stu-id="b61ab-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="b61ab-127">Zestawom E i F udzielono uprawnienia P1A.</span><span class="sxs-lookup"><span data-stu-id="b61ab-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="b61ab-128">Zestawowi C udzielono uprawnienia P1.</span><span class="sxs-lookup"><span data-stu-id="b61ab-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="b61ab-129">Do zestawów A i B nie udzielono uprawnień P1 ani P1A.</span><span class="sxs-lookup"><span data-stu-id="b61ab-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="b61ab-130">Metoda A jest zawarta w zestawie A, metoda B jest zawarta w zestawie B i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b61ab-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram przedstawiający zestawy metod Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="b61ab-132">W tym scenariuszu Metoda A wywołuje wywołania B, B wywołuje C, C wywołuje E, i E wywołuje metodę F. Metoda C potwierdza uprawnienie do odczytu plików na dysku C (uprawnienie P1), a metoda E wymaga uprawnień do odczytu plików txt na dysku C (uprawnienia P1A).</span><span class="sxs-lookup"><span data-stu-id="b61ab-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="b61ab-133">Gdy w czasie wykonywania zostanie napotkane żądanie w języku F, zostanie wykonane badanie stosu w celu sprawdzenia uprawnień wszystkich wywołujących F, zaczynając od E. E, przyznano uprawnienia P1A, więc stos przeprowadzi badanie uprawnień C, gdzie wykryto potwierdzenie języka C.</span><span class="sxs-lookup"><span data-stu-id="b61ab-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="b61ab-134">Ponieważ uprawnienie żądanie (P1A) jest podzbiorem potwierdzonego uprawnienia (P1), przechodzenie przez stos zostanie zatrzymane i sprawdzanie zabezpieczeń zostanie automatycznie zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b61ab-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="b61ab-135">Nie ma znaczenia, że zestawy A i B nie uzyskały uprawnień P1A.</span><span class="sxs-lookup"><span data-stu-id="b61ab-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="b61ab-136">Przez poproszenie P1, metoda C zapewnia, że jej obiekty wywołujące mogą uzyskać dostęp do zasobów chronionych przez P1, nawet jeśli nie udzielono uprawnień dostępu do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="b61ab-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="b61ab-137">W przypadku projektowania biblioteki klas i uzyskiwania dostępu do chronionego zasobu należy w większości przypadków zapewnić zapotrzebowanie na zabezpieczenia wymagające, aby wywołujący klasę mieli odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b61ab-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="b61ab-138">Jeśli klasa następnie wykonuje operację, dla której wiadomo, że większość jej obiektów wywołujących nie ma uprawnień, a jeśli wolisz podjąć odpowiedzialność za zezwolenie tym wywołującemu na wywoływanie kodu, możesz postanowić się, wywołując metodę **Assert** na Obiekt uprawnień, który reprezentuje operację wykonywaną przez kod.</span><span class="sxs-lookup"><span data-stu-id="b61ab-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="b61ab-139">Użycie metody **Assert** w ten sposób umożliwia wywoływanie, że zwykle nie można to wywołać w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b61ab-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="b61ab-140">W związku z tym, jeśli zostanie potwierdzone uprawnienie, należy upewnić się, że odpowiednie sprawdzenia zabezpieczeń zostały wcześniej wykonane, aby zapobiec nieprawidłowemu użyciu składnika.</span><span class="sxs-lookup"><span data-stu-id="b61ab-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="b61ab-141">Załóżmy na przykład, że Klasa wysoce zaufanej biblioteki ma metodę, która usuwa pliki.</span><span class="sxs-lookup"><span data-stu-id="b61ab-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="b61ab-142">Uzyskuje dostęp do pliku, wywołując niezarządzaną funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="b61ab-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="b61ab-143">Obiekt wywołujący wywołuje metodę **usuwania** kodu, przekazując nazwę pliku do usunięcia, C:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="b61ab-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="b61ab-144">W ramach metody **delete** kod tworzy <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący dostęp do zapisu do C:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="b61ab-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="b61ab-145">(Dostęp do zapisu jest wymagany do usunięcia pliku). Kod następnie wywołuje bezwzględne sprawdzenie zabezpieczeń, wywołując metodę **żądania** obiektu **FileIOPermission** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="b61ab-146">Jeśli jeden z obiektów wywołujących w stosie wywołań nie ma tego uprawnienia, <xref:System.Security.SecurityException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="b61ab-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="b61ab-147">Jeśli żaden wyjątek nie zostanie zgłoszony, wiadomo, że wszyscy wywołujący mają prawo dostępu do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="b61ab-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="b61ab-148">Ponieważ sądzisz, że większość obiektów wywołujących nie będzie miała uprawnień dostępu do kodu niezarządzanego, kod następnie tworzy <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje prawo do wywoływania kodu niezarządzanego i wywołuje metodę **Assert** obiektu.</span><span class="sxs-lookup"><span data-stu-id="b61ab-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="b61ab-149">Na koniec wywołuje niezarządzaną funkcję Win32 w celu usunięcia C:\Text.txt i zwraca kontrolę do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b61ab-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b61ab-150">Musisz się upewnić, że Twój kod nie używa potwierdzeń w sytuacjach, w których kod może być używany przez inny kod w celu uzyskania dostępu do zasobu chronionego przez żądane uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="b61ab-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="b61ab-151">Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez obiekt wywołujący jako parametr, nie **FileIOPermission** do zapisu w plikach, ponieważ kod może być otwarty do niewłaściwego użycia przez inną firmę.</span><span class="sxs-lookup"><span data-stu-id="b61ab-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="b61ab-152">W przypadku użycia bezwzględnej składni zabezpieczenia wywoływanie metody **Assert** dla wielu uprawnień w tej samej metodzie powoduje zgłoszenie wyjątku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="b61ab-153">Zamiast tego należy utworzyć obiekt **PermissionSet** , przekazać mu poszczególne uprawnienia, które mają zostać wywołane, a następnie wywołać metodę **Assert** dla obiektu **PermissionSet** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="b61ab-154">Metodę **Assert** można wywołać więcej niż raz w przypadku użycia deklaratywnej składni zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="b61ab-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="b61ab-155">Poniższy przykład pokazuje deklaratywną składnię zastępowania kontroli zabezpieczeń przy użyciu metody **Assert** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="b61ab-156">Należy zauważyć, że składnia **FileIOPermissionAttribute** przyjmuje dwie wartości: <xref:System.Security.Permissions.SecurityAction> Wyliczenie i lokalizację pliku lub katalogu, do którego ma zostać udzielone uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="b61ab-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="b61ab-157">Wywołanie metody **Assert** powoduje, że wymagania dostępu `C:\Log.txt` do programu powiodło się, nawet jeśli obiekty wywołujące nie są sprawdzane w celu uzyskania uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="b61ab-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="b61ab-158">Poniższe fragmenty kodu przedstawiają nieprawidłową składnię do zastępowania kontroli zabezpieczeń przy użyciu metody **Assert** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="b61ab-159">W tym przykładzie jest zadeklarowane wystąpienie obiektu **FileIOPermission** .</span><span class="sxs-lookup"><span data-stu-id="b61ab-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="b61ab-160">Jego Konstruktor został przesłany jako **FileIOPermissionAccess. AllAccess** , aby można było zdefiniować dozwolony typ dostępu, po którym następuje ciąg opisujący lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="b61ab-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="b61ab-161">Po zdefiniowaniu obiektu **FileIOPermission** należy wywołać jego metodę **Assert** , aby zastąpić sprawdzanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b61ab-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b61ab-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b61ab-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="b61ab-163">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b61ab-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="b61ab-164">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="b61ab-164">Code Access Security</span></span>](code-access-security.md)
