---
title: Mapowanie nazw algorytmów na klasy kryptografii
description: Mapowanie nazw algorytmów na klasy kryptografii w programie .NET. Deweloper ma cztery opcje tworzenia obiektu kryptografii.
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 5a1d7acdd34182dd82f4dce66d136c4ef4de6e95
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105355"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapowanie nazw algorytmów na klasy kryptografii
Istnieją cztery sposoby tworzenia obiektu kryptografii przez dewelopera przy użyciu Windows SDK:  
  
- Utwórz obiekt za pomocą operatora **New** .  
  
- Utwórz obiekt implementujący określony algorytm kryptograficzny przez wywołanie metody **Create** dla tego algorytmu w klasie abstrakcyjnej.  
  
- Utwórz obiekt implementujący określony algorytm kryptograficzny przez wywołanie <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.  
  
- Utwórz obiekt, który implementuje klasę algorytmów kryptograficznych (na przykład szyfr bloku symetrycznego) przez wywołanie metody **Create** w klasie abstrakcyjnej dla tego typu algorytmu (na przykład <xref:System.Security.Cryptography.SymmetricAlgorithm> ).  
  
 Załóżmy na przykład, że deweloper chce obliczyć Skrót SHA1 zestawu bajtów. <xref:System.Security.Cryptography>Przestrzeń nazw zawiera dwie implementacje algorytmu SHA1, jedną czysto zarządzaną implementację i jedną, która zawija interfejs CryptoAPI. Deweloper może zdecydować się na utworzenie wystąpienia określonej implementacji SHA1 (np <xref:System.Security.Cryptography.SHA1Managed> .) przez wywołanie operatora **New** . Jednakże jeśli nie ma znaczenia, które klasy są ładowane przez środowisko uruchomieniowe języka wspólnego, o ile Klasa implementuje algorytm skrótu SHA1, deweloper może utworzyć obiekt, wywołując <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metodę. Ta metoda wywołuje metodę **System. Security. Cryptography. obiektu CryptoConfig. isfrom ("System. Security. Cryptography. SHA1")**, która musi zwracać implementację algorytmu wyznaczania wartości skrótu SHA1.  
  
 Deweloper może również wywołać metodę **System. Security. Cryptography. obiektu CryptoConfig. isfrom ("SHA1")** , ponieważ domyślnie konfiguracja kryptografii zawiera krótkie nazwy dla algorytmów dostarczonych w .NET Framework.  
  
 Jeśli nie ma znaczenia, który algorytm wyznaczania wartości skrótu jest używany, programista może wywołać <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metodę, która zwraca obiekt implementujący transformację mieszania.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapowanie nazw algorytmów w plikach konfiguracji  
 Domyślnie środowisko uruchomieniowe zwraca <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> obiekt dla wszystkich czterech scenariuszy. Jednak administrator komputera może zmienić typ obiektu, który zwracają metody z ostatnich dwóch scenariuszy. W tym celu należy zmapować przyjazną nazwę algorytmu na klasę, która ma być używana w pliku konfiguracyjnym komputera (Machine.config).  
  
 Poniższy przykład pokazuje, jak skonfigurować środowisko uruchomieniowe, tak aby **System. Security. Cryptography. SHA1. Create**, **System. Security. obiektu CryptoConfig. isfromname ("SHA1")** i **System. Security. Cryptography. algorytm. Create** zwraca `MySHA1HashClass` obiekt.  
  
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
  
 Możesz określić nazwę atrybutu w [<cryptoClass \> elementu](./file-schema/cryptography/cryptoclass-element.md) (w poprzednim przykładzie nazwa atrybutu `MySHA1Hash` ). Wartość atrybutu w **\<cryptoClass>** elemencie jest ciągiem, który jest wykorzystywany przez środowisko uruchomieniowe języka wspólnego do znajdowania klasy. Można użyć dowolnego ciągu, który spełnia wymagania określone w polu [Określanie w pełni kwalifikowanych nazw typów](../reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Wiele nazw algorytmów można zamapować na tę samą klasę. [ \<nameEntry> Element](./file-schema/cryptography/nameentry-element.md) mapuje klasę na jedną przyjazną nazwę algorytmu. Atrybut **name** może być ciągiem, który jest używany podczas wywoływania metody **System. Security. Cryptography. obiektu CryptoConfig. isfromname** lub nazwy klasy abstrakcyjnej kryptografii w <xref:System.Security.Cryptography> przestrzeni nazw. Wartość atrybutu **Class** to nazwa atrybutu w **\<cryptoClass>** elemencie.  
  
> [!NOTE]
> Algorytm SHA1 można uzyskać, wywołując <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metodę or metody **Security. obiektu CryptoConfig. setfrom ("SHA1")** . Każda metoda gwarantuje tylko, że zwraca obiekt, który implementuje algorytm SHA1. Nie ma potrzeby mapowania poszczególnych przyjaznych nazw algorytmów do tej samej klasy w pliku konfiguracji.  
  
 Aby uzyskać listę domyślnych nazw i klas, do których są mapowane, zobacz <xref:System.Security.Cryptography.CryptoConfig> .  
  
## <a name="see-also"></a>Zobacz też

- [Usługi kryptograficzne](../../standard/security/cryptographic-services.md)
- [Konfigurowanie klasy kryptografii](configure-cryptography-classes.md)
