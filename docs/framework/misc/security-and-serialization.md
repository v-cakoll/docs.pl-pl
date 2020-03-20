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
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181117"
---
# <a name="security-and-serialization"></a><span data-ttu-id="0d80b-102">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="0d80b-102">Security and Serialization</span></span>
<span data-ttu-id="0d80b-103">Ponieważ serializacja może zezwolić na inne dane wystąpienia lub modyfikowania, które w przeciwnym razie byłyby niedostępne, wymagane jest specjalne uprawnienie do wykonywania serializacji kodu: <xref:System.Security.Permissions.SecurityPermission> z określoną <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flagą.</span><span class="sxs-lookup"><span data-stu-id="0d80b-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="0d80b-104">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="0d80b-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="0d80b-105">Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych szeregowanych dla wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0d80b-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="0d80b-106">Jest możliwe dla kodu, który można interpretować format, aby określić, jakie są wartości danych, niezależnie od dostępności elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0d80b-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="0d80b-107">Podobnie deserializacji wyodrębnia dane z serializowanej reprezentacji i ustawia stan obiektu bezpośrednio, ponownie niezależnie od reguł ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0d80b-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="0d80b-108">Każdy obiekt, który może zawierać dane wrażliwe na zabezpieczenia powinny być nieuprzejme, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0d80b-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="0d80b-109">Jeśli musi być serializable, spróbuj zrobić określone pola, które przechowują poufne dane nienaserializalne.</span><span class="sxs-lookup"><span data-stu-id="0d80b-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="0d80b-110">Jeśli nie można tego zrobić, należy pamiętać, że te dane będą narażone na każdy kod, który ma uprawnienia do serializacji i upewnij się, że żaden złośliwy kod może uzyskać to uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="0d80b-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="0d80b-111">Interfejs <xref:System.Runtime.Serialization.ISerializable> jest przeznaczony do użytku tylko przez infrastrukturę serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d80b-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="0d80b-112">Jednak jeśli nie jest chroniony, może potencjalnie zwolnić poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="0d80b-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="0d80b-113">Jeśli podasz niestandardową serializację, implementując **ISerializable,** upewnij się, że podjęto następujące środki ostrożności:</span><span class="sxs-lookup"><span data-stu-id="0d80b-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="0d80b-114">Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> powinna być jawnie zabezpieczone przez żądanie **SecurityPermission** z **SerializationFormatter** uprawnienia określone lub upewniając się, że żadne poufne informacje są zwalniane z danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="0d80b-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="0d80b-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0d80b-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="0d80b-116">Specjalny konstruktor używany do serializacji należy również wykonać dokładne sprawdzanie poprawności danych wejściowych i powinny być chronione lub prywatne, aby pomóc chronić przed niewłaściwym użyciem przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="0d80b-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="0d80b-117">Należy wymusić te same kontrole zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takiej klasy za pomocą innych środków, takich jak jawne tworzenie klasy lub pośrednio tworzenie go za pośrednictwem pewnego rodzaju fabryki.</span><span class="sxs-lookup"><span data-stu-id="0d80b-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d80b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d80b-118">See also</span></span>

- [<span data-ttu-id="0d80b-119">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="0d80b-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
