---
title: Mapowanie nazw algorytmów na klasy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 6ec98aabd92a7a0fed11482bdf6e5e8ddc045a7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098744"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="15a9d-102">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="15a9d-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="15a9d-103">Istnieją cztery sposoby Deweloper można utworzyć obiektu kryptografii przy użyciu [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="15a9d-103">There are four ways a developer can create a cryptography object using the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span></span>  
  
-   <span data-ttu-id="15a9d-104">Utwórz obiekt przy użyciu **nowe** operatora.</span><span class="sxs-lookup"><span data-stu-id="15a9d-104">Create an object by using the **new** operator.</span></span>  
  
-   <span data-ttu-id="15a9d-105">Utwórz wystąpienie obiektu implementującego na algorytm kryptograficzny określonego przez wywołanie metody **Utwórz** metody abstrakcyjne klasy dla tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="15a9d-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
-   <span data-ttu-id="15a9d-106">Utwórz wystąpienie obiektu implementującego na algorytm kryptograficzny określonego przez wywołanie metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="15a9d-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="15a9d-107">Utwórz obiekt, który implementuje klasa algorytmów kryptograficznych (takich jak symetrycznym szyfrem) przez wywołanie metody **Utwórz** metody abstrakcyjne klasy dla tego typu algorytmu (takie jak <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="15a9d-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="15a9d-108">Na przykład załóżmy, że deweloper chce obliczenia skrótu SHA1 zestawu bajtów.</span><span class="sxs-lookup"><span data-stu-id="15a9d-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="15a9d-109"><xref:System.Security.Cryptography> Przestrzeń nazw zawiera dwie implementacje algorytmu SHA1, co czysto zarządzaną implementację i jedną, która opakowuje interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="15a9d-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="15a9d-110">Deweloper można wybrać do utworzenia wystąpienia określonej implementacji SHA1 (takie jak <xref:System.Security.Cryptography.SHA1Managed>) przez wywołanie metody **nowe** operatora.</span><span class="sxs-lookup"><span data-stu-id="15a9d-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="15a9d-111">Jednak jeśli nie ma znaczenia, klasa, która ładuje środowisko uruchomieniowe języka wspólnego, tak długo, jak klasa implementuje algorytm wyznaczania wartości skrótu SHA1, deweloper można utworzyć obiektu przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="15a9d-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="15a9d-112">Ta metoda wywołuje **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, który musi zwrócić implementację algorytmu wyznaczania wartości skrótu SHA1.</span><span class="sxs-lookup"><span data-stu-id="15a9d-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="15a9d-113">Deweloper można również wywołać **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** ponieważ domyślnie kryptografii Konfiguracja obejmuje krótkich nazw dla algorytmów dostarczane w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15a9d-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="15a9d-114">Jeśli jest używany algorytm wyznaczania wartości skrótu, który nie ma znaczenia, deweloper może wywołać <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metody, która zwraca obiekt, który implementuje przekształcania wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="15a9d-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="15a9d-115">Mapowanie nazw algorytmów w plikach konfiguracji</span><span class="sxs-lookup"><span data-stu-id="15a9d-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="15a9d-116">Domyślnie środowisko wykonawcze zwraca <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> obiektu dla wszystkich, cztery scenariusze.</span><span class="sxs-lookup"><span data-stu-id="15a9d-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="15a9d-117">Jednak administrator komputera można zmienić typu obiektu, zwracane metod w ostatnich dwóch scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="15a9d-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="15a9d-118">Aby to zrobić, należy zamapować algorytm przyjazną nazwę klasy, których chcesz użyć w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="15a9d-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="15a9d-119">Poniższy przykład przedstawia sposób konfigurowania środowiska uruchomieniowego, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, i  **System.Security.Cryptography.HashAlgorithm.Create** zwracają `MySHA1HashClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="15a9d-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="15a9d-120">Możesz określić nazwę atrybutu w [< cryptoclass —\> elementu](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (poprzedni przykład nazwy atrybutu `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="15a9d-120">You can specify the name of the attribute in the [<cryptoClass\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="15a9d-121">Wartość atrybutu w  **\<cryptoclass — >** element stanowi ciąg, który używa środowiska uruchomieniowego języka wspólnego, można znaleźć klasy.</span><span class="sxs-lookup"><span data-stu-id="15a9d-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="15a9d-122">Można użyć dowolnego ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="15a9d-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="15a9d-123">Wiele nazw algorytm można mapować do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="15a9d-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="15a9d-124">[ \<Nameentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapuje klasy jeden algorytm przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="15a9d-124">The [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="15a9d-125">**Nazwa** atrybut może być ciąg, który jest używany podczas wywoływania **System.Security.Cryptography.CryptoConfig.CreateFromName** metody lub nazwę klasy abstrakcyjnej kryptografii w <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="15a9d-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="15a9d-126">Wartość **klasy** atrybut jest nazwą atrybutu w  **\<cryptoclass — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="15a9d-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15a9d-127">Algorytm SHA1 można uzyskać przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> lub **Security.CryptoConfig.CreateFromName("SHA1")** metody.</span><span class="sxs-lookup"><span data-stu-id="15a9d-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="15a9d-128">Każda metoda gwarantuje tylko zwraca obiekt, który implementuje algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="15a9d-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="15a9d-129">Nie masz mapowania każdego przyjazna nazwa algorytmu do tej samej klasy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="15a9d-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="15a9d-130">Aby uzyskać listę domyślnych nazw i klas mapowania ich na, zobacz <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="15a9d-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a9d-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15a9d-131">See also</span></span>

- [<span data-ttu-id="15a9d-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="15a9d-132">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="15a9d-133">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="15a9d-133">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
