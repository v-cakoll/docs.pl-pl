---
title: Mapowanie nazw algorytmów na klasy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912869"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="ff119-102">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="ff119-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="ff119-103">Istnieją cztery sposoby tworzenia obiektu kryptografii przez dewelopera przy użyciu Windows SDK:</span><span class="sxs-lookup"><span data-stu-id="ff119-103">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="ff119-104">Utwórz obiekt za pomocą operatora **New** .</span><span class="sxs-lookup"><span data-stu-id="ff119-104">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="ff119-105">Utwórz obiekt implementujący określony algorytm kryptograficzny przez wywołanie metody **Create** dla tego algorytmu w klasie abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="ff119-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="ff119-106">Utwórz obiekt implementujący określony algorytm kryptograficzny przez wywołanie <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ff119-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ff119-107">Utwórz obiekt, który implementuje klasę algorytmów kryptograficznych (na przykład szyfr bloku symetrycznego) przez wywołanie metody **Create** w klasie abstrakcyjnej dla tego typu algorytmu (na przykład <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="ff119-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="ff119-108">Załóżmy na przykład, że deweloper chce obliczyć Skrót SHA1 zestawu bajtów.</span><span class="sxs-lookup"><span data-stu-id="ff119-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="ff119-109"><xref:System.Security.Cryptography> Przestrzeń nazw zawiera dwie implementacje algorytmu SHA1, jedną czysto zarządzaną implementację i jedną, która zawija interfejs CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="ff119-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="ff119-110">Deweloper może zdecydować się na utworzenie wystąpienia określonej implementacji SHA1 (np <xref:System.Security.Cryptography.SHA1Managed>.) przez wywołanie operatora **New** .</span><span class="sxs-lookup"><span data-stu-id="ff119-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="ff119-111">Jednakże jeśli nie ma znaczenia, które klasy są ładowane przez środowisko uruchomieniowe języka wspólnego, o ile Klasa implementuje algorytm skrótu SHA1, deweloper może utworzyć obiekt, wywołując <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="ff119-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ff119-112">Ta metoda wywołuje metodę **System. Security. Cryptography. obiektu CryptoConfig. isfrom ("System. Security. Cryptography. SHA1")** , która musi zwracać implementację algorytmu wyznaczania wartości skrótu SHA1.</span><span class="sxs-lookup"><span data-stu-id="ff119-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="ff119-113">Deweloper może również wywołać metodę **System. Security. Cryptography. obiektu CryptoConfig. isfrom ("SHA1")** , ponieważ domyślnie konfiguracja kryptografii zawiera krótkie nazwy dla algorytmów dostarczonych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff119-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="ff119-114">Jeśli nie ma znaczenia, który algorytm wyznaczania wartości skrótu jest używany, programista może wywołać <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metodę, która zwraca obiekt implementujący transformację mieszania.</span><span class="sxs-lookup"><span data-stu-id="ff119-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="ff119-115">Mapowanie nazw algorytmów w plikach konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ff119-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="ff119-116">Domyślnie środowisko uruchomieniowe zwraca <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> obiekt dla wszystkich czterech scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ff119-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="ff119-117">Jednak administrator komputera może zmienić typ obiektu, który zwracają metody z ostatnich dwóch scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ff119-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="ff119-118">W tym celu należy zmapować przyjazną nazwę algorytmu na klasę, która ma być używana w pliku konfiguracyjnym komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ff119-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="ff119-119">Poniższy przykład pokazuje, jak skonfigurować środowisko uruchomieniowe w taki sposób, aby **System. Security. Cryptography. SHA1. Create**, **System. Security. obiektu CryptoConfig. isfromname ("SHA1")** i **System. Security. Cryptography. algorytm. Create zwraca obiekt.** `MySHA1HashClass`</span><span class="sxs-lookup"><span data-stu-id="ff119-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
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
  
 <span data-ttu-id="ff119-120">Możesz określić nazwę atrybutu w [\> < cryptoClass elementu](./file-schema/cryptography/cryptoclass-element.md) (w poprzednim przykładzie nazwa atrybutu `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="ff119-120">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="ff119-121">Wartość atrybutu w  **\<elemencie cryptoClass >** jest ciągiem, który jest wykorzystywany przez środowisko uruchomieniowe języka wspólnego do znajdowania klasy.</span><span class="sxs-lookup"><span data-stu-id="ff119-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="ff119-122">Można użyć dowolnego ciągu, który spełnia wymagania określone w polu [Określanie w pełni kwalifikowanych nazw typów](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ff119-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="ff119-123">Wiele nazw algorytmów można zamapować na tę samą klasę.</span><span class="sxs-lookup"><span data-stu-id="ff119-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="ff119-124">Element nameEntry > mapuje klasę na jedną przyjazną nazwę algorytmu. [ \<](./file-schema/cryptography/nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff119-124">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="ff119-125">Atrybut **name** może być ciągiem, który jest używany podczas wywoływania metody **System. Security. Cryptography. obiektu CryptoConfig.** isfromname lub nazwy <xref:System.Security.Cryptography> klasy abstrakcyjnej kryptografii w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ff119-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="ff119-126">Wartość atrybutu **Class** to nazwa atrybutu w  **\<elemencie cryptoClass >** .</span><span class="sxs-lookup"><span data-stu-id="ff119-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff119-127">Algorytm SHA1 można uzyskać, wywołując <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metodę or metody **Security. obiektu CryptoConfig. setfrom ("SHA1")** .</span><span class="sxs-lookup"><span data-stu-id="ff119-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="ff119-128">Każda metoda gwarantuje tylko, że zwraca obiekt, który implementuje algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="ff119-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="ff119-129">Nie ma potrzeby mapowania poszczególnych przyjaznych nazw algorytmów do tej samej klasy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff119-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="ff119-130">Aby uzyskać listę domyślnych nazw i klas, do których są mapowane, zobacz <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="ff119-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff119-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff119-131">See also</span></span>

- [<span data-ttu-id="ff119-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="ff119-132">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ff119-133">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="ff119-133">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
