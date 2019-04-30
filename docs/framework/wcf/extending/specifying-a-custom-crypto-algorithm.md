---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: b365c3c8e74adcad03246a227d6593c49f8b3993
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768709"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="b5fa2-102">Określanie niestandardowego algorytmu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="b5fa2-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="b5fa2-103">WCF umożliwia określanie niestandardowego algorytmu kryptograficznego do użycia podczas szyfrowania danych lub przetwarzania podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="b5fa2-104">Jest to realizowane przez następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b5fa2-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="b5fa2-105">Wyprowadzić klasę z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="b5fa2-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="b5fa2-106">Rejestrowanie algorytmu</span><span class="sxs-lookup"><span data-stu-id="b5fa2-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="b5fa2-107">Konfigurowanie powiązania z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="b5fa2-108">Wyprowadzenia klasy z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="b5fa2-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="b5fa2-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Jest abstrakcyjną klasę bazową, która pozwala na Określanie algorytmu do użycia podczas przeprowadzania zabezpieczeń różnych operacji związanych z.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="b5fa2-110">Na przykład obliczanie skrótu do podpisu cyfrowego lub szyfrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="b5fa2-111">Poniższy kod przedstawia sposób wyprowadzić klasę z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="b5fa2-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="b5fa2-112">Rejestrowanie niestandardowego algorytmu</span><span class="sxs-lookup"><span data-stu-id="b5fa2-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="b5fa2-113">Rejestracja może odbywać się w pliku konfiguracji lub kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="b5fa2-114">Rejestrowanie niestandardowego algorytmu odbywa się przez utworzenie mapowanie między klasę, która implementuje dostawcę usług kryptograficznych i alias.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="b5fa2-115">Alias jest następnie mapowany do identyfikatora URI, który jest używany podczas określania algorytm w powiązaniu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="b5fa2-116">Poniższy fragment kodu konfiguracji przedstawia sposób rejestrowania niestandardowego algorytmu w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b5fa2-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
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
  
 <span data-ttu-id="b5fa2-117">W sekcji <`cryptoClasses`> element tworzy mapowanie między SHA256CryptoServiceProvider i alias "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="b5fa2-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="b5fa2-118"><`nameEntry`> Element tworzy mapowanie między aliasu "SHA256CSP" i pod określony adres URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="b5fa2-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="b5fa2-119">Do rejestrowania niestandardowego algorytmu używany kod <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metody.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="b5fa2-120">Ta metoda tworzy oba mapowania.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-120">This method creates both mappings.</span></span> <span data-ttu-id="b5fa2-121">Poniższy przykład pokazuje, jak wywołać tę metodę:</span><span class="sxs-lookup"><span data-stu-id="b5fa2-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="b5fa2-122">Konfigurowanie powiązania</span><span class="sxs-lookup"><span data-stu-id="b5fa2-122">Configure the Binding</span></span>  
 <span data-ttu-id="b5fa2-123">Konfigurowanie powiązania, określając niestandardowy <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-pochodne klasy w ustawieniach powiązania, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="b5fa2-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="b5fa2-124">Aby uzyskać pełny przykład kodu, zobacz [Zręczność kryptograficzna w zabezpieczeniach WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="b5fa2-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fa2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5fa2-125">See also</span></span>

- [<span data-ttu-id="b5fa2-126">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b5fa2-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b5fa2-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="b5fa2-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="b5fa2-128">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b5fa2-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="b5fa2-129">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b5fa2-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
