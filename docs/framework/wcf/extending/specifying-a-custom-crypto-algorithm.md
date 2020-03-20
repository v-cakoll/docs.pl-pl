---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186486"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="4a03d-102">Określanie niestandardowego algorytmu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="4a03d-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="4a03d-103">WCF umożliwia określenie niestandardowego algorytmu kryptograficznego używanego podczas szyfrowania danych lub przetwarzania podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="4a03d-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="4a03d-104">Odbywa się to w następujących krokach:</span><span class="sxs-lookup"><span data-stu-id="4a03d-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="4a03d-105">Wyprowadz klasę z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="4a03d-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="4a03d-106">Zarejestruj algorytm</span><span class="sxs-lookup"><span data-stu-id="4a03d-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="4a03d-107">Skonfiguruj <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>powiązanie z klasą pochodną.</span><span class="sxs-lookup"><span data-stu-id="4a03d-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="4a03d-108">Czerpanie klasy z SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="4a03d-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="4a03d-109">Jest <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> abstrakcyjną klasą podstawową, która umożliwia określenie algorytmu do użycia podczas wykonywania różnych operacji związanych z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="4a03d-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="4a03d-110">Na przykład obliczanie skrótu dla podpisu cyfrowego lub szyfrowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4a03d-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="4a03d-111">Poniższy kod pokazuje, jak wyprowadzić klasę z: <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="4a03d-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="4a03d-112">Zarejestruj algorytm niestandardowy</span><span class="sxs-lookup"><span data-stu-id="4a03d-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="4a03d-113">Rejestracja może odbywać się w pliku konfiguracyjnym lub w kodzie imperatywnym.</span><span class="sxs-lookup"><span data-stu-id="4a03d-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="4a03d-114">Rejestrowanie niestandardowego algorytmu odbywa się przez utworzenie mapowania między klasą, która implementuje dostawcę usług kryptograficznych i alias.</span><span class="sxs-lookup"><span data-stu-id="4a03d-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="4a03d-115">Alias jest następnie mapowane do identyfikatora URI, który jest używany podczas określania algorytmu w powiązanie usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4a03d-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="4a03d-116">Poniższy fragment kodu konfiguracji ilustruje sposób rejestrowania niestandardowego algorytmu w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4a03d-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
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
  
 <span data-ttu-id="4a03d-117">Sekcja w <`cryptoClasses`> element tworzy mapowanie między SHA256CryptoServiceProvider i alias "SHA256CSP".</span><span class="sxs-lookup"><span data-stu-id="4a03d-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="4a03d-118">Element <`nameEntry`> tworzy mapowanie między aliasem "SHA256CSP" a określonym `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`adresem URL .</span><span class="sxs-lookup"><span data-stu-id="4a03d-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="4a03d-119">Aby zarejestrować niestandardowy algorytm <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> w kodzie należy użyć metody.</span><span class="sxs-lookup"><span data-stu-id="4a03d-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="4a03d-120">Ta metoda tworzy oba mapowania.</span><span class="sxs-lookup"><span data-stu-id="4a03d-120">This method creates both mappings.</span></span> <span data-ttu-id="4a03d-121">W poniższym przykładzie pokazano, jak wywołać tę metodę:</span><span class="sxs-lookup"><span data-stu-id="4a03d-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="4a03d-122">Konfigurowanie powiązania</span><span class="sxs-lookup"><span data-stu-id="4a03d-122">Configure the Binding</span></span>  
 <span data-ttu-id="4a03d-123">Powiązanie można skonfigurować, określając <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>niestandardową klasę pochodną w ustawieniach powiązania, jak pokazano w poniższym fragmentie kodu:</span><span class="sxs-lookup"><span data-stu-id="4a03d-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="4a03d-124">Aby uzyskać przykład pełnego kodu, zobacz [kryptograficzne agility w WCF security](../samples/cryptographic-agility-in-wcf-security.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="4a03d-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a03d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a03d-125">See also</span></span>

- [<span data-ttu-id="4a03d-126">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4a03d-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4a03d-127">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="4a03d-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="4a03d-128">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4a03d-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="4a03d-129">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4a03d-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
