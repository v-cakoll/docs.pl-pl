---
title: <xmlSerializer>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: b83ecda30bba8af1f3175eb6ad08593b07a80e6c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249542"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="1d251-102">\<xmlSerializer> Element</span><span class="sxs-lookup"><span data-stu-id="1d251-102">\<xmlSerializer> Element</span></span>
<span data-ttu-id="1d251-103">Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="1d251-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="1d251-104">\<> konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="1d251-104">\<configuration></span></span>  
<span data-ttu-id="1d251-105">\<> system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="1d251-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d251-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d251-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d251-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d251-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1d251-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d251-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d251-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d251-109">Attributes</span></span>  
  
|<span data-ttu-id="1d251-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d251-110">Attribute</span></span>|<span data-ttu-id="1d251-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1d251-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d251-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="1d251-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="1d251-113">Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="1d251-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="1d251-114">Atrybut "prawda" lub "false".</span><span class="sxs-lookup"><span data-stu-id="1d251-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="1d251-115">Wartość domyślna to "true".</span><span class="sxs-lookup"><span data-stu-id="1d251-115">The default is "true".</span></span>|  
|<span data-ttu-id="1d251-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="1d251-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="1d251-117">Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d251-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="1d251-118">Wartość domyślna to **false**.</span><span class="sxs-lookup"><span data-stu-id="1d251-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d251-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d251-119">Child Elements</span></span>  
 <span data-ttu-id="1d251-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d251-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d251-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d251-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1d251-122">Element</span><span class="sxs-lookup"><span data-stu-id="1d251-122">Element</span></span>|<span data-ttu-id="1d251-123">Opis</span><span class="sxs-lookup"><span data-stu-id="1d251-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d251-124">\<element> system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="1d251-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="1d251-125">Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d251-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d251-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d251-126">Remarks</span></span>  
 <span data-ttu-id="1d251-127">Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="1d251-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="1d251-128">Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="1d251-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="1d251-129">Jeśli taki warunek zostanie wykryty, wyjątek jest zgłaszany z następującym komunikatem: "Błąd wewnętrzny: deserializacja nie może przejść przez podstawowy strumień."</span><span class="sxs-lookup"><span data-stu-id="1d251-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="1d251-130">Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku.</span><span class="sxs-lookup"><span data-stu-id="1d251-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="1d251-131">W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="1d251-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="1d251-132">Jeśli okaże się, że w danej aplikacji uzasadnione komunikaty są odrzucane przez tę dodatkową warstwę ochrony, ustaw **atrybut checkDeserializeAdvances** na "false".</span><span class="sxs-lookup"><span data-stu-id="1d251-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d251-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d251-133">Example</span></span>  
 <span data-ttu-id="1d251-134">Poniższy przykład kodu ustawia **checkDeserializeAdvances** atrybut "false".</span><span class="sxs-lookup"><span data-stu-id="1d251-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d251-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d251-135">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="1d251-136">\<element> system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="1d251-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="1d251-137">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="1d251-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
