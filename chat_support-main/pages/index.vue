<template>
    <div class="min-h-screen bg-[#F8FAFC] flex items-center justify-center px-4 py-12">
      <!-- Success Notification Banner -->
      <div v-if="showPurchaseSuccess" class="fixed top-4 inset-x-0 flex justify-center z-50">
        <div class="bg-white rounded-lg shadow-md border border-green-100 p-4 max-w-md flex items-center space-x-3 animate-slide-down">
          <div class="flex-shrink-0 bg-green-100 rounded-full p-1">
            <svg class="h-5 w-5 text-green-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
            </svg>
          </div>
          <div class="flex-1">
            <p class="text-sm font-medium text-gray-900">Purchase successful!</p>
            <p class="text-xs text-gray-600">Your account is ready. Access all features now.</p>
          </div>
          <div class="flex space-x-2">
            
            <button 
              @click="showPurchaseSuccess = false" 
              class="text-gray-400 hover:text-gray-600">
              <svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
              </svg>
            </button>
          </div>
        </div>
      </div>
      
      <!-- Login Form Container -->
      <div class="w-full max-w-sm mx-auto">
        <div class="p-8 bg-white rounded-xl shadow-sm border border-gray-100">
          <!-- Logo -->
          <div class="flex items-center gap-2 mb-8">

            <span class="text-xl font-medium text-gray-900">Chatbot Support</span>
          </div>
  
          <!-- Title and Description -->
          <div class="space-y-2 mb-8">
            <h1 class="text-2xl font-medium text-gray-900">
              Hello!
            </h1>
            <p class="text-gray-600">
              Sign in to your account to continue
            </p>
          </div>
  
          <!-- Google Login Button -->
  
          <NuxtLink to="/main/id_1234" class="w-full flex items-center justify-center gap-3 py-2.5 rounded-lg border border-gray-200 text-gray-700 hover:bg-gray-50 transition-colors relative">
            Access App
          </NuxtLink>
  


          <!-- <button
            @click="handleGoogleLogin"
            :disabled="isLoading"
            class="w-full flex items-center justify-center gap-3 px-4 py-2.5 rounded-lg border border-gray-200 text-gray-700 hover:bg-gray-50 transition-colors relative"
          >
            <span class="absolute left-4">
              <svg class="w-5 h-5" viewBox="0 0 24 24">
                <path
                  d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"
                  fill="#4285F4"
                />
                <path
                  d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"
                  fill="#34A853"
                />
                <path
                  d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"
                  fill="#FBBC05"
                />
                <path
                  d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"
                  fill="#EA4335"
                />
              </svg>
            </span>
            <span class="text-sm font-medium">
              {{ isLoading ? 'Signing in...' : 'Continue with Google' }}
            </span>
          </button> -->
  
          <!-- Terms Notice -->
          <!-- <p class="mt-8 text-xs text-center text-gray-500">
            By continuing, you agree to our
            <a href="" class="text-blue-500 hover:text-blue-600">Terms of Service</a>
            and
            <a href="" class="text-blue-500 hover:text-blue-600">Privacy Policy</a>
          </p> -->
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  const router = useRoute()
  import { ArrowRight } from 'lucide-vue-next';
  import { navigateTo } from '#app'
  
  const isLoading = ref(false);
  const showPurchaseSuccess = ref(false);
  onMounted(() => {
    if(router.query.checkout_success) {
      showPurchaseSuccess.value = true;
    }
  })
  
  import PocketBase from 'pocketbase';
  
  const auth_data_ref = ref()
  const pb = new PocketBase('https://chatbot-support-pocketbase.fly.dev');
  
  definePageMeta({
    layout: false
  })
  
  const handleGoogleLogin = () => {
    isLoading.value = true;
    // Here you would implement the actual Google OAuth login
    // For now just simulating the loading state
    console.log('line 79')
  
  console.log('line 85')
    let w = window.open()
  console.log('line 87')
   const auth_data = pb.collection("users")
      .authWithOAuth2({
        provider: 'google',
        urlCallback: (url) => {
          // @ts-ignore
            w.location.href = url
        },
      })
  
      auth_data_ref.value = auth_data
  
      
  };
  
  watch(auth_data_ref, async (newVal) => {
  
    const handleCheckoutCreem = async (id_user: string, product_name: string, product_id: string) : Promise<{success: boolean, message: string, content: string}> => {
    const data = await $fetch('/api/get_checkout', {
      method: 'POST',
      body: {
        id_user: id_user,
        product_name: product_name,
        product_id: product_id
      }
    })
  
    console.log('line 207 - we got the checkout data', data)
    return data
  }
  
    try {
      let w_meta = await newVal;
      if (w_meta.meta.isNew) {
        console.log('New user detected');
        let user_id = w_meta.record.id;
        
  
        if(router.query.product_id && router.query.product_name) {
          console.log('line 147 (about to call checkoutcreem) - we got a product_id and product_name', router.query.product_id, router.query.product_name)
          const checkout_data = await handleCheckoutCreem(user_id, router.query.product_name as string, router.query.product_id as string)
  
          if(checkout_data.success) {
            navigateTo(checkout_data.content, {
              external: true,
            })
          }else{
            console.error('line 141 - we got an error from the checkout call', checkout_data)
          }
  
  
        } else {
          navigateTo('/welcome/' + user_id)
        }
  
      } else if (!w_meta.meta.isNew) {
  
        let user_id = w_meta.record.id;
  
  
        const check_if_user_has_trial =  (user_record: any) : boolean => { 
            let id_merchant_subscription = user_record['id_merchant_subscription']
  
            return id_merchant_subscription == null || id_merchant_subscription == '' ? true : false
         }
        let has_query_params = router.query.product_id && router.query.product_name ? true : false
        let has_trial = check_if_user_has_trial(w_meta.record) // The record we receive is from the users collection - the main collection
  
  
        if(has_query_params && has_trial) {
  
          const checkout_data = await handleCheckoutCreem(user_id, router.query.product_name as string, router.query.product_id as string)
  
          if(checkout_data.success) {
            navigateTo(checkout_data.content, {
              external: true,
            })
          }
  
          }else if(has_query_params && !has_trial){
            navigateTo('/billing')
          }else if(!has_query_params && !has_trial){
            navigateTo('/projects')
          }else if(!has_query_params && has_trial){
            navigateTo('/projects')
          }
  
        }
      }catch(error){
        console.error('Error in watch handler:', error);
      }
  });
  
  
  
  </script>
  
  <style scoped>
  .min-h-screen {
    min-height: 100vh;
  }
  
  button:disabled {
    opacity: 0.7;
    cursor: not-allowed;
  }
  
  .animate-slide-down {
    animation: slideDown 0.3s ease-out;
  }
  
  @keyframes slideDown {
    from {
      opacity: 0;
      transform: translateY(-20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  </style>