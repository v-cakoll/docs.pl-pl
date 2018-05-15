---
title: Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 6309f312ed05f48e65b19d8827322071cad1f6de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="2e551-102">Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e551-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="2e551-103">Mimo że `My.Computer.Registry` powinno obejmować potrzeb podstawowe, gdy Programowanie w odniesieniu do rejestru, można również użyć <xref:Microsoft.Win32.Registry> i <xref:Microsoft.Win32.RegistryKey> klas w <xref:Microsoft.Win32> przestrzeń nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e551-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="2e551-104">Klucze rejestru klasy</span><span class="sxs-lookup"><span data-stu-id="2e551-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="2e551-105"><xref:Microsoft.Win32.Registry> Klasa zapewnia kluczy rejestru podstawowej, które mogą być używane do dostępu podklucze i ich wartości.</span><span class="sxs-lookup"><span data-stu-id="2e551-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="2e551-106">Podstawowy samych kluczy są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="2e551-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="2e551-107">Poniższej tabeli wymieniono i opisano klucze siedmiu udostępnianych przez <xref:Microsoft.Win32.Registry> klasy.</span><span class="sxs-lookup"><span data-stu-id="2e551-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="2e551-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="2e551-108">**Key**</span></span>|<span data-ttu-id="2e551-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2e551-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="2e551-110">Określa typy dokumentów i właściwości skojarzone z tych typów.</span><span class="sxs-lookup"><span data-stu-id="2e551-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="2e551-111">Zawiera informacje o konfiguracji sprzętu, który nie jest specyficzne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e551-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="2e551-112">Zawiera informacje o bieżącym preferencje użytkownika, takie jak zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="2e551-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="2e551-113">Zawiera dane rejestru dynamicznych, takie jak używany przez sterowniki urządzeń wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="2e551-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="2e551-114">Zawiera pięć podkluczy (sprzętu, SAM zabezpieczeń, oprogramowania i systemu) zawierających dane konfiguracji na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="2e551-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="2e551-115">Zawiera informacje o wydajności dla składników oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="2e551-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="2e551-116">Zawiera informacje o domyślnych preferencji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e551-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e551-117">Jest bardziej bezpieczne można zapisać danych do bieżącego użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>) niż do komputera lokalnego (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="2e551-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="2e551-118">Warunek, który jest zwykle nazywany "tureckie" występuje podczas tworzenia klucza wcześniej została utworzona przez inny proces potencjalnie szkodliwymi.</span><span class="sxs-lookup"><span data-stu-id="2e551-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="2e551-119">Aby temu zapobiec, należy użyć metody, takie jak <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, która zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2e551-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="2e551-120">Odczytywanie wartości z rejestru</span><span class="sxs-lookup"><span data-stu-id="2e551-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="2e551-121">Poniższy kod przedstawia sposób odczytywania ciąg z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2e551-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 <span data-ttu-id="2e551-122">Poniższy kod odczytuje zwiększa, a następnie zapisuje ciąg do HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2e551-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2e551-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e551-123">See Also</span></span>  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="2e551-124">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e551-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="2e551-125">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="2e551-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="2e551-126">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="2e551-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
