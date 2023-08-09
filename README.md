# Proxy-Service

En proxy som konverterer studentoppføringer frem og tilbake mellom et XML-format og et binært format.

Scenarioet er strippet ned til de helt grunnleggende funksjonene. Det er et eksempel avsender av
studentoppføring i XML-format kalt xmlSender, en annen som sender poster i binært format kalt binSender, 
og en mottaker som enten kan motta XML eller binært format kalt anyReceiver. Senderne leser fra disk, mottakeren skriver til disk.

Alle disse kobles til proxyen, som fungerer som en TCP-server. Når en avsender leser en post fra disk,
sender den den til proxyen. Proxyen konverterer denne oppføringen til et internt format og kontrollerer
destinasjons-ID-en i den posten. Hvis det er en node med denne IDen koblet til proxyen, konverterer
proxyen oppføringen til formatet (XML eller binært) som er passende for denne noden og sender den.

Proxyen støtter alle kombinasjoner: XML sender - XML receiver, XML sender - binary receiver, binary
sender - XML receiver, binary sender - binary receiver.
