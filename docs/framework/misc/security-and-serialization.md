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
ms.openlocfilehash: e4deadc175bd4cc3635a6c8d8d8b80100b5a9938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868839"
---
# <a name="security-and-serialization"></a><span data-ttu-id="b3573-102">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="b3573-102">Security and Serialization</span></span>
<span data-ttu-id="b3573-103">Ponieważ serializacji może pozwalać na inny kod wyświetlić lub zmodyfikować dane wystąpienia obiektu, która mogłaby być niedostępna, specjalne uprawnienie jest wymagane wykonywanie serializacji kodu: <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> określono flagę.</span><span class="sxs-lookup"><span data-stu-id="b3573-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="b3573-104">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b3573-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="b3573-105">Normalnie wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych serializacji dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b3573-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="b3573-106">Istnieje możliwość dla kodu, który może interpretować formatu, aby ustalić, jakie wartości danych są, niezależnie od dostępności członka.</span><span class="sxs-lookup"><span data-stu-id="b3573-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="b3573-107">Podobnie deserializacji wyodrębnia dane z zserializowana reprezentacja i ustawia stan obiektu bezpośrednio, ponownie niezależnie od zasady ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="b3573-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="b3573-108">Dowolny obiekt, który może zawierać dane istotnymi dla zabezpieczeń należy nonserializable, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b3573-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="b3573-109">Jeśli muszą podlegać serializacji, spróbuj wprowadzić określonych pól zawierających dane poufne nonserializable.</span><span class="sxs-lookup"><span data-stu-id="b3573-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="b3573-110">Jeśli nie jest to możliwe, należy pamiętać, że te dane będą widoczne wszelki kod, który ma uprawnienia do serializacji i upewnij się, czy nie złośliwego kodu można uzyskać to uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="b3573-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="b3573-111"><xref:System.Runtime.Serialization.ISerializable> Interfejsu jest przeznaczony do użytku tylko przez infrastrukturę serializacji.</span><span class="sxs-lookup"><span data-stu-id="b3573-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="b3573-112">Jednak jeśli bez ochrony, jego potencjalnie zwalniać poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="b3573-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="b3573-113">Jeśli podasz niestandardowej serializacji implementując **ISerializable**, upewnij się, należy wykonać następujące środki ostrożności:</span><span class="sxs-lookup"><span data-stu-id="b3573-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="b3573-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody powinny być jawnie zabezpieczone przez wymagających **SecurityPermission** z **SerializationFormatter** uprawnienie określono lub przez upewniając się, że nie liter informacje o zwolnieniu z danymi wyjściowymi metody.</span><span class="sxs-lookup"><span data-stu-id="b3573-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="b3573-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b3573-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="b3573-116">Specjalnych konstruktora, używanych na potrzeby serializowania również należy wykonać dokładne sprawdzenie poprawności danych wejściowych i powinna być chroniona lub prywatnej, aby chronić przed niewłaściwym użyciem przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="b3573-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="b3573-117">Powinien on wymuszać samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienia takich klasy za pomocą innych środków, takich jak jawne utworzenie klasy lub pośrednio ją przy użyciu pewnego rodzaju fabryki.</span><span class="sxs-lookup"><span data-stu-id="b3573-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3573-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3573-118">See also</span></span>

- [<span data-ttu-id="b3573-119">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b3573-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
