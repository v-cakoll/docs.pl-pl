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
ms.openlocfilehash: e0b1f8979929dbb6872bbd53e1840b2d0520a31d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910672"
---
# <a name="security-and-serialization"></a><span data-ttu-id="b5cb8-102">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="b5cb8-102">Security and Serialization</span></span>
<span data-ttu-id="b5cb8-103">Ponieważ Serializacja może zezwalać innemu kodowi na wyświetlanie lub modyfikowanie danych wystąpienia obiektu, które w przeciwnym razie byłyby niedostępne, wymagane jest specjalne uprawnienie do kodu <xref:System.Security.Permissions.SecurityPermission> wykonującego <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> serializacji: z określoną flagą.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="b5cb8-104">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="b5cb8-105">Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w serializowanych danych dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="b5cb8-106">Możliwe jest, że kod, który może interpretować format, aby określić, jakie wartości danych są niezależne od dostępności elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="b5cb8-107">Podobnie deserializacja wyodrębnia dane z serializowanej reprezentacji i bezpośrednio ustawia stan obiektu, niezależnie od zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="b5cb8-108">Każdy obiekt, który może zawierać dane zależne od zabezpieczeń, powinien być niemożliwy do serializacji, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="b5cb8-109">Jeśli musi to być możliwe do serializacji, spróbuj wprowadzić określone pola, które mają dane poufne, które nie mogą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="b5cb8-110">Jeśli nie można tego zrobić, należy pamiętać, że te dane zostaną uwidocznione w dowolnym kodzie, który ma uprawnienia do serializacji, i upewnić się, że żaden złośliwy kod nie może uzyskać tego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="b5cb8-111"><xref:System.Runtime.Serialization.ISerializable> Interfejs jest przeznaczony do użytku tylko przez infrastrukturę serializacji.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="b5cb8-112">Jednak w przypadku niechronionego programu może on potencjalnie zwolnić poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="b5cb8-113">W przypadku zapewnienia serializacji niestandardowej przez implementację interfejsu **ISerializable**upewnij się, że są wykonywane następujące środki ostrożności:</span><span class="sxs-lookup"><span data-stu-id="b5cb8-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="b5cb8-114">Metoda powinna być jawnie zabezpieczona przez wymaganie SecurityPermission z uprawnieniami **SerializationFormatter** określonymi lub przez zapewnienie, że żadne poufne informacje nie są zwalniane za pomocą metody danych wyjściowych. <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A></span><span class="sxs-lookup"><span data-stu-id="b5cb8-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="b5cb8-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b5cb8-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="b5cb8-116">Specjalny Konstruktor używany do serializacji powinien również wykonywać dokładne sprawdzanie poprawności danych wejściowych i powinien być chroniony lub prywatny, aby pomóc w ochronie przed nieprawidłowym użyciem złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="b5cb8-117">Należy wymusić te same sprawdzenia zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takiej klasy w inny sposób, na przykład w celu jawnego utworzenia klasy lub pośredniego tworzenia jej za pośrednictwem pewnego rodzaju fabryki.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cb8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5cb8-118">See also</span></span>

- [<span data-ttu-id="b5cb8-119">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b5cb8-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
