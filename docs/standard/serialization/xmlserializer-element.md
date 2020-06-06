---
title: <xmlSerializer> Element
description: <xmlSerializer>Element określa, czy jest wykonywane dodatkowe sprawdzanie postępu elementu XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288930"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="5d74a-103">\<xmlSerializer> Element</span><span class="sxs-lookup"><span data-stu-id="5d74a-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="5d74a-104">Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="5d74a-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="5d74a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d74a-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d74a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d74a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5d74a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d74a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d74a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d74a-108">Attributes</span></span>  
  
|<span data-ttu-id="5d74a-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5d74a-109">Attribute</span></span>|<span data-ttu-id="5d74a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5d74a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d74a-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="5d74a-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="5d74a-112">Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="5d74a-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="5d74a-113">Atrybut "prawda" lub "false".</span><span class="sxs-lookup"><span data-stu-id="5d74a-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="5d74a-114">Wartość domyślna to "true".</span><span class="sxs-lookup"><span data-stu-id="5d74a-114">The default is "true".</span></span>|  
|<span data-ttu-id="5d74a-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="5d74a-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="5d74a-116">Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="5d74a-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="5d74a-117">Wartość domyślna to **false**.</span><span class="sxs-lookup"><span data-stu-id="5d74a-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d74a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d74a-118">Child Elements</span></span>  
 <span data-ttu-id="5d74a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d74a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d74a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d74a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5d74a-121">Element</span><span class="sxs-lookup"><span data-stu-id="5d74a-121">Element</span></span>|<span data-ttu-id="5d74a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5d74a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d74a-123">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="5d74a-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="5d74a-124">Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d74a-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d74a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d74a-125">Remarks</span></span>  
 <span data-ttu-id="5d74a-126">Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="5d74a-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="5d74a-127">Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="5d74a-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="5d74a-128">W przypadku wykrycia takiego warunku zostanie zgłoszony wyjątek z następującym komunikatem: "błąd wewnętrzny: deserializacja nie powiodła się przed strumieniem bazowym".</span><span class="sxs-lookup"><span data-stu-id="5d74a-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="5d74a-129">Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku.</span><span class="sxs-lookup"><span data-stu-id="5d74a-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="5d74a-130">W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="5d74a-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="5d74a-131">Jeśli okaże się, że w konkretnej aplikacji legalne komunikaty są odrzucane przez tę dodatkową warstwę ochrony, ustaw atrybut **checkDeserializeAdvances** na wartość "false".</span><span class="sxs-lookup"><span data-stu-id="5d74a-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d74a-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d74a-132">Example</span></span>  
 <span data-ttu-id="5d74a-133">Poniższy przykład kodu ustawia atrybut **checkDeserializeAdvances** na wartość "false".</span><span class="sxs-lookup"><span data-stu-id="5d74a-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d74a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d74a-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="5d74a-135">\<system.xml.serialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="5d74a-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="5d74a-136">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="5d74a-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
