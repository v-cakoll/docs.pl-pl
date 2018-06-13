---
title: Zabezpieczenia i serializacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a30e80b1b4a412405787c0c14ad58995a2d7fffc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394251"
---
# <a name="security-and-serialization"></a><span data-ttu-id="43cf6-102">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="43cf6-102">Security and Serialization</span></span>
<span data-ttu-id="43cf6-103">Ponieważ serializacji można zezwolić na inny kod, aby wyświetlić lub zmodyfikować danych wystąpienia obiektów, które w przeciwnym razie będą niedostępne, specjalnych uprawnień jest wymagane kodu wykonywania serializacji: <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> określona flaga.</span><span class="sxs-lookup"><span data-stu-id="43cf6-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="43cf6-104">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="43cf6-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="43cf6-105">Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych serializacji dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="43cf6-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="43cf6-106">Istnieje możliwość kod umożliwiający interpretowanie formatu, aby ustalić, jakie wartości danych są, niezależnie od dostępności elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="43cf6-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="43cf6-107">Podobnie deserializacji wyodrębnia dane z zserializowana reprezentacja i ustawia stan obiektu bezpośrednio, ponownie niezależnie od zasady ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="43cf6-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="43cf6-108">Każdy obiekt, który może zawierać danych istotnych dla zabezpieczeń należy nonserializable, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="43cf6-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="43cf6-109">Jeśli muszą podlegać serializacji, spróbuj wprowadzić określonych pól, które zawierają dane poufne nonserializable.</span><span class="sxs-lookup"><span data-stu-id="43cf6-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="43cf6-110">Jeśli nie jest to możliwe, należy pamiętać, że te dane mają być widoczne do kodu, który ma uprawnienia do serializacji i gwarancja, że nie złośliwego kodu to uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="43cf6-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="43cf6-111"><xref:System.Runtime.Serialization.ISerializable> Interfejsu jest przeznaczony do użytku tylko przez infrastrukturę serializacji.</span><span class="sxs-lookup"><span data-stu-id="43cf6-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="43cf6-112">Jednak jeśli niechronionej, jego potencjalnie zwolnić poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="43cf6-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="43cf6-113">Jeśli podasz niestandardowej serializacji zaimplementowanie **ISerializable**, upewnij się, podejmij następujące środki ostrożności:</span><span class="sxs-lookup"><span data-stu-id="43cf6-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="43cf6-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody powinny być jawnie zabezpieczone przez wymagających **SecurityPermission** z **SerializationFormatter** uprawnienia określone lub przez upewniając się, że nie liter informacje o zwolnieniu z danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="43cf6-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="43cf6-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="43cf6-115">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
-   <span data-ttu-id="43cf6-116">Specjalne Konstruktor używany do serializacji należy przeprowadzić dokładne sprawdzania poprawności danych wejściowych i powinien być chroniona lub prywatnej w celu ochrony przed niewłaściwym użyciem przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="43cf6-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="43cf6-117">Należy go wymuszać te same testy zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takich klasy w inny sposób, takie jak jawne utworzenie klasy lub pośrednio przy użyciu określonego rodzaju fabryki.</span><span class="sxs-lookup"><span data-stu-id="43cf6-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cf6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43cf6-118">See Also</span></span>  
 [<span data-ttu-id="43cf6-119">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="43cf6-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
