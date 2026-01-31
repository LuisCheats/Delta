<div align='center'>@7noonly/Delta - API de WhatsApp Web</div>

<div align="center">
  <img src="https://nexy-ar7z.b-cdn.net/storage/b99a0660.jpg" alt="7Noonly" width="300" style="border-radius: 20px;"/>
</div>

Nota Importante

ꕤ Esta librería está basada en Baileys y ha sido personalizada con mucho amor por 7Noonly. No está afiliada con WhatsApp.

Aviso de Responsabilidad

@7noonly/Delta y su desarrollador no pueden ser responsables por mal uso.  
Por favor, usa esta librería para crear cosas lindas y positivas, no para spam o actividades maliciosas.

Instalación

# Versión estable  
npm install @7noonly/Delta  
# o  
yarn add @7noonly/Delta  

# Versión de desarrollo  
npm install github:7noonly/Delta  
# o  
yarn add github:7noonly/Delta

Ejemplo Rápido en JavaScript

const { makeWASocket, useMultiFileAuthState } = require('@7noonly/Delta')

async function startBot() {
    const { state, saveCreds } = await useMultiFileAuthState('session-7noonly')

    const noonly = makeWASocket({
        auth: state,
        printQRInTerminal: true
    })

    noonly.ev.on('connection.update', ({ connection }) => {
        if (connection === 'open') {
            console.log('¡Conectado con éxito!')
        }
    })

    noonly.ev.on('messages.upsert', async ({ messages }) => {
        const m = messages[0]
        if (m.message) {
            await noonly.sendMessage(m.key.remoteJid, {
                text: '¡Hola! Soy un bot de Delta!'
            })
        }
    })

    noonly.ev.on('creds.update', saveCreds)
}

startBot()

Ejemplo Rápido en TypeScript

import makeWASocket, { useMultiFileAuthState } from '@7noonly/Delta'

async function startBot(): Promise<void> {
    const { state, saveCreds } = await useMultiFileAuthState('session-7noonly')

    const noonly = makeWASocket({
        auth: state,
        printQRInTerminal: true
    })

    noonly.ev.on('connection.update', ({ connection }) => {
        if (connection === 'open') {
            console.log('¡Conectado con éxito!')
        }
    })

    noonly.ev.on('messages.upsert', async ({ messages }) => {
        const m = messages[0]
        if (m.message) {
            await noonly.sendMessage(m.key.remoteJid!, {
                text: '¡Hola! Soy un bot de Delta!'
            })
        }
    })

    noonly.ev.on('creds.update', saveCreds)
}

startBot()

Características Principales

· Optimizado para mayor velocidad y estabilidad  
· Mensajes multimedia  
· Comandos personalizados fáciles de implementar  
· Soporte para grupos y chats privados  
· Mensajes interactivos con botones  

Funciones Técnicas

· Conexión estable con reconexión automática  
· Sesiones persistentes que se guardan solitas  
· Manejo de errores con mensajes bonitos  
· Sincronización en tiempo real  

Características Técnicas

· Sin Selenium – Conexión directa vía WebSocket  
· Súper eficiente – Ahorra mucha RAM  
· Soporte multi-dispositivo – Compatible con la versión web  
· Totalmente tipado – Con TypeScript y JavaScript  
· API completa – Todas las funciones de WhatsApp Web  
· Rendimiento optimizado – Código eficiente y rápido  

Uso Básico

Inicializar el Bot (JavaScript)

const { makeWASocket, useMultiFileAuthState } = require('@7noonly/Delta')

const { state, saveCreds } = await useMultiFileAuthState('session-7noonly')
const noonly = makeWASocket({
    auth: state,
    printQRInTerminal: true
})

noonly.ev.on('creds.update', saveCreds)

Inicializar el Bot (TypeScript)

import makeWASocket, { useMultiFileAuthState } from '@7noonly/Delta'

const { state, saveCreds } = await useMultiFileAuthState('session-7noonly')
const noonly = makeWASocket({
    auth: state,
    printQRInTerminal: true
})

noonly.ev.on('creds.update', saveCreds)

Enviar Mensajes

// Mensaje de texto  
await noonly.sendMessage(jid, { text: '¡Hola mundo!' })

// Imagen con caption  
await noonly.sendMessage(jid, {
    image: { url: './images/7noonly.jpg' },
    caption: '¡Mira mi nueva foto!'
})

// Sticker  
await noonly.sendMessage(jid, {
    sticker: { url: './stickers/7noonly.webp' }
})

Comandos Personalizados

JavaScript

noonly.ev.on('messages.upsert', async ({ messages }) => {
    const m = messages[0]
    const text = m.message?.conversation || m.message?.extendedTextMessage?.text

    if (text === '!hola') {
        await noonly.sendMessage(m.key.remoteJid, {
            text: '¡Hola! Soy Delta, ¿en qué puedo ayudarte?'
        })
    }
})

TypeScript

noonly.ev.on('messages.upsert', async ({ messages }) => {
    const m = messages[0]
    const text = m.message?.conversation || m.message?.extendedTextMessage?.text

    if (text === '!hola') {
        await noonly.sendMessage(m.key.remoteJid!, {
            text: '¡Hola! Soy 7Noonly, ¿en qué puedo ayudarte?'
        })
    }
})

Configuración Avanzada

const noonly = makeWASocket({
    auth: state,
    printQRInTerminal: true,
    markOnlineOnConnect: false,
    browser: ["Delta", "Chrome", "1.0.0"],
    logger: require('pino')({ level: 'silent' })
})

Ejemplos de Funciones

Enviar Mensaje a Múltiples Chats

async function broadcastMessage(jids, message) {
    for (const jid of jids) {
        await noonly.sendMessage(jid, { text: message })
    }
}

Descargar Medios

const { downloadMediaMessage } = require('@7noonly/Delta')

const stream = await downloadMediaMessage(message, 'buffer')

Tipos para TypeScript

import { WAMessage, WASocket } from '@7noonly/Delta'

interface MyBot extends WASocket {
    // Tus tipos personalizados aquí
}

function handleMessage(message: WAMessage): void {
    // Tu lógica de manejo de mensajes
}

---

<div align="center">Powered by 7Noonly ✰</div>