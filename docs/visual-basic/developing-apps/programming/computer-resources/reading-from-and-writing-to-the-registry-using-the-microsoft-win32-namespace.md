---
title: Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345498"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="b63e1-102">Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b63e1-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="b63e1-103">Chociaż `My.Computer.Registry` powinny obejmować podstawowe potrzeby podczas programowania w rejestrze, można również użyć klas <xref:Microsoft.Win32.Registry> i <xref:Microsoft.Win32.RegistryKey> w przestrzeni nazw <xref:Microsoft.Win32> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b63e1-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="b63e1-104">Klucze w klasie rejestru</span><span class="sxs-lookup"><span data-stu-id="b63e1-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="b63e1-105">Klasa <xref:Microsoft.Win32.Registry> dostarcza podstawowych kluczy rejestru, których można użyć w celu uzyskania dostępu do podkluczy i ich wartości.</span><span class="sxs-lookup"><span data-stu-id="b63e1-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="b63e1-106">Same klucze podstawowe są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b63e1-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="b63e1-107">W poniższej tabeli wymieniono i opisano siedem kluczy uwidacznianych przez klasę <xref:Microsoft.Win32.Registry>.</span><span class="sxs-lookup"><span data-stu-id="b63e1-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="b63e1-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="b63e1-108">**Key**</span></span>|<span data-ttu-id="b63e1-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b63e1-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="b63e1-110">Definiuje typy dokumentów i właściwości skojarzone z tymi typami.</span><span class="sxs-lookup"><span data-stu-id="b63e1-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="b63e1-111">Zawiera informacje o konfiguracji sprzętu, które nie są specyficzne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b63e1-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="b63e1-112">Zawiera informacje o bieżących preferencjach użytkownika, takich jak zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="b63e1-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="b63e1-113">Zawiera dynamiczne dane rejestru, takie jak używane przez sterowniki urządzeń wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="b63e1-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="b63e1-114">Zawiera pięć podkluczy (sprzęt, SAM, zabezpieczenia, oprogramowanie i system) przechowujących dane konfiguracji dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b63e1-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="b63e1-115">Zawiera informacje o wydajności składników oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="b63e1-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="b63e1-116">Zawiera informacje o domyślnych preferencjach użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b63e1-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="b63e1-117">Bardziej bezpieczne jest zapisanie danych do bieżącego użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>) niż na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="b63e1-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="b63e1-118">Warunek, który jest zwykle określany jako "squatting", występuje, gdy tworzony klucz został wcześniej utworzony przez inny, prawdopodobnie złośliwy, proces.</span><span class="sxs-lookup"><span data-stu-id="b63e1-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="b63e1-119">Aby temu zapobiec, użyj metody, takiej jak <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, która zwraca `Nothing`, jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b63e1-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="b63e1-120">Odczytywanie wartości z rejestru</span><span class="sxs-lookup"><span data-stu-id="b63e1-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="b63e1-121">Poniższy kod ilustruje sposób odczytywania ciągu z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="b63e1-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="b63e1-122">Poniższy kod odczytuje, zwiększa, a następnie zapisuje ciąg do HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="b63e1-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="b63e1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b63e1-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="b63e1-124">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b63e1-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b63e1-125">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="b63e1-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="b63e1-126">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="b63e1-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
