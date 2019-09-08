---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: cf4b3da82087a6daade9d6b939f3e1aac628cb01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796892"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="c7794-102">Określanie niestandardowego algorytmu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="c7794-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="c7794-103">Usługa WCF umożliwia określenie niestandardowego algorytmu kryptograficznego, który ma być używany podczas szyfrowania danych lub przetwarzania podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="c7794-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="c7794-104">W tym celu należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c7794-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="c7794-105">Utwórz klasę z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="c7794-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="c7794-106">Rejestrowanie algorytmu</span><span class="sxs-lookup"><span data-stu-id="c7794-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="c7794-107">Skonfiguruj powiązanie z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>klasą pochodną.</span><span class="sxs-lookup"><span data-stu-id="c7794-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="c7794-108">Utwórz klasę z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c7794-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="c7794-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Jest abstrakcyjną klasą bazową, która pozwala określić algorytm, który ma być używany podczas wykonywania różnych operacji związanych z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="c7794-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="c7794-110">Na przykład Obliczanie skrótu podpisu cyfrowego lub szyfrowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7794-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="c7794-111">Poniższy kod przedstawia sposób wygenerowania klasy z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="c7794-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="c7794-112">Rejestrowanie niestandardowego algorytmu</span><span class="sxs-lookup"><span data-stu-id="c7794-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="c7794-113">Rejestrację można przeprowadzić w pliku konfiguracji lub w bezwzględnym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7794-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="c7794-114">Zarejestrowanie algorytmu niestandardowego odbywa się przez utworzenie mapowania między klasą, która implementuje dostawcę usług kryptograficznych i alias.</span><span class="sxs-lookup"><span data-stu-id="c7794-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="c7794-115">Alias jest następnie mapowany na identyfikator URI, który jest używany podczas określania algorytmu w powiązaniu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c7794-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="c7794-116">Poniższy fragment konfiguracji ilustruje sposób rejestrowania niestandardowego algorytmu w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="c7794-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="c7794-117">Sekcja w <`cryptoClasses`elementu > tworzy mapowanie między SHA256CryptoServiceProvider i aliasem "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="c7794-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="c7794-118"><`nameEntry`Element > tworzy mapowanie między aliasem "SHA256CSP" i określonym adresem URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="c7794-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="c7794-119">Aby zarejestrować niestandardowy algorytm w kodzie, <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> Użyj metody.</span><span class="sxs-lookup"><span data-stu-id="c7794-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="c7794-120">Ta metoda powoduje utworzenie obu mapowań.</span><span class="sxs-lookup"><span data-stu-id="c7794-120">This method creates both mappings.</span></span> <span data-ttu-id="c7794-121">Poniższy przykład pokazuje, jak wywołać tę metodę:</span><span class="sxs-lookup"><span data-stu-id="c7794-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="c7794-122">Konfigurowanie powiązania</span><span class="sxs-lookup"><span data-stu-id="c7794-122">Configure the Binding</span></span>  
 <span data-ttu-id="c7794-123">Powiązanie można skonfigurować przez określenie klasy pochodnej niestandardowej <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>w ustawieniach powiązań, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="c7794-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="c7794-124">Aby uzyskać kompletny przykład kodu, zobacz [elastyczność kryptograficzną w przykładowym zabezpieczeniu WCF](../samples/cryptographic-agility-in-wcf-security.md) .</span><span class="sxs-lookup"><span data-stu-id="c7794-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7794-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7794-125">See also</span></span>

- [<span data-ttu-id="c7794-126">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c7794-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c7794-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="c7794-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="c7794-128">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c7794-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="c7794-129">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c7794-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
